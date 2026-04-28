---
name: humanizer
description: Reviews any written content for AI-generated
  patterns, scores it, and rewrites it in an authentic
  human voice. Auto-detects content type (blog, LinkedIn,
  email, Slack). Reads VOICE-AND-STYLE.md to calibrate
  to the user's specific voice. Use whenever creating
  user-facing external content or when the user asks to
  humanize, review, or check writing.
triggers:
  - "humanize"
  - "does this sound like AI"
  - "rewrite in my voice"
  - "check this email"
  - "LinkedIn post review"
  - "blog review"
  - creating external-facing content
  - output destination is "human-facing external"
model: claude-sonnet-4-6
---

# The Humanizer

Detect AI texture. Score authenticity. Rewrite in
the user's actual voice.

## Invocation context

Check how this skill was called before proceeding:

**Draft review mode** (user invoked directly):
- Confirm detected content type to user
- Close rewrite with: "Your edits on top of this
  are often the best version."
- Present the full review report

**Direct output mode** (invoked by output-validator
with context="direct_output"):
- Skip detection confirmation — apply rules silently
- Skip the closing "your edits" line
- Skip the full review report unless output-validator
  requests it
- Deliver clean rewritten content ready to embed
  directly into the tool or output

---

## Step 0 — Load voice profile

Before anything else, read VOICE-AND-STYLE.md.

Extract:
- PREFERRED_TONE
- RESPONSE_LENGTH_PREFERENCE
- INFORMATION_STYLE
- THINGS_I_LIKE (in writing)
- THINGS_I_DISLIKE (in writing)
- STANDING_PREFERENCES
- WRITING_SAMPLES (if any)

If in draft review mode and VOICE-AND-STYLE.md has
no writing-specific entries, ask once:
"To calibrate to your voice, it helps to see 1-3
paragraphs from your own writing that feel most
like you. Optional — paste anything or skip."

Store any provided samples in VOICE-AND-STYLE.md
under WRITING_SAMPLES.

If in direct output mode: use what's available
without asking.

## Step 1 — Auto-detect content type

**Email** — ANY of:
- Subject line, To:/From:/CC: headers
- Greeting formula ("Hi [Name]", "Dear [Name]")
- Formal sign-off followed by name
- "I wanted to reach out", "Following up"

**LinkedIn** — ANY of:
- One-sentence-per-line paragraph formatting
- Hashtags (#topic)
- Engagement CTA at end ("Thoughts?", "Agree?")
- Under 3,000 characters with no headings

**Slack** — ANY of:
- @mentions or #channel references
- Under 500 characters, conversational fragments
- No greeting or sign-off

**Blog post** — ANY of:
- Headings or subheadings
- 3,000+ characters of structured prose
- Multiple developed paragraphs

Default to blog if ambiguous.

In draft review mode only: state detection and
invite correction.
In direct output mode: apply silently.

## Step 2 — AI pattern scan

### Universal phrase-level markers — flag every instance

**AI vocabulary:**
delve, leverage (as verb), transformative, game-changing,
seamless, robust, synergy, best practices, thought leader,
landscape, paradigm, harness, navigate, unlock, empower,
streamline, holistic, tapestry, multifaceted, nuanced,
foster, cultivate, facilitate, utilize, comprehensive,
albeit, whilst, superpower, journey, reality (as dramatic
reveal), elevate, realm, essentially, certainly, overall
(as filler qualifier), absolutely (as affirmation opener),
typically, various (as vague pluralizer), insights

**AI transitions and openers:**
"Furthermore", "Moreover", "In conclusion", "Additionally",
"It's worth noting", "in summary" (mid-content),
"In today's [noun]", "When it comes to",
"At the end of the day", "The truth is" (before generic claim),
"It goes without saying", "It's important to note that"

**AI phrasing and metaphors:**
"brutal clarity", "lost the plot", "painfully clear",
"with precision", "lived experience", "laying the groundwork",
"will never be the same", "that promise becomes reality",
"not only...but also", "here's a breakdown",
"in the ever-evolving landscape", "a testament to",
"Below is..." / "Below:" as list intro,
"such as" repeated as examples connector

**AI structural markers:**
- Opens with generic claim instead of specific story
- Every paragraph roughly same length
- Bullet structure where prose would carry more weight
- Intro > 3-point list > conclusion template
- Summary closing instead of challenge or principle
- Three-part parallel: "It's not about X. It's about Y."
- Stacked fragments: "X. Y. Z." as punchlines
- Self-posed question transition: "Why? Because..."
- Declarative reveal: "The skill that will separate...? X."
- Punchy orphan closer: standalone mic-drop line
- Triple rhetorical question opener
- Honesty disclaimer: "And I'll be honest:" / "I'll be real:"
- Credential stacking opener
- Stat bomb opener (3+ rapid statistical fragments)
- Standalone hype fragment: "This is big."
- Passive voice where active would be stronger
- Runway sentences (vague hype before the actual point)
- Stacked abstract noun lists (3+ for emotional weight)

### LinkedIn-specific markers

**Phrase-level:**
- Pivot transitions: "But here's the thing", "Here's the kicker"
- Engagement bait: "Agree?", "Thoughts?", "Repost if this resonates"
- Vulnerability performance: "I'll be honest", "Can I be real?"
- Fake humility: "I'm no expert, but..."
- Arrow chains: → → → format
- ALL-CAPS single-word injection for emphasis
- "What if I told you..." hook
- "Here's what nobody tells you about..." (without insider knowledge)
- "Read that again." / "Let that sink in."
- "And honestly?" before non-controversial claim
- Tag-and-thank lists of 5+ people

**Structural:**
- One-line-per-paragraph formatting throughout
- Information-withheld hook (can't tell what post is about)
- Common-belief-then-counter opener (template tension)
- Period-separated word emphasis ("every. single. day.")
- Self-intro paragraph at post bottom
- Achievement post: emotion word + announcement + team thanks
  + generic lesson + emoji sign-off (all four beats = template)
- Fake dialogue between two roles (CEO/CMO, etc.)

### Email-specific markers

**Phrase-level:**
- AI greetings: "I hope this email finds you well"
- AI closings: "Please don't hesitate to reach out"
- Corporate filler: "I wanted to reach out because",
  "Per our previous conversation", "Going forward"
- Hedge language: "I was wondering if perhaps"
- AI vocabulary: "circle back", "loop in", "touch base",
  "sync up", "deep dive", "bandwidth"

**Structural:**
- More than one ask
- Ask buried at the bottom
- 2-3x longer than needed
- Vague CTA instead of specific
- Multiple sign-offs stacked

### Slack-specific markers

- Over-formal language for casual medium
- Unnecessary hedging ("Sorry to bother you, but...")
- Emoji overload (3+ in short message)
- More than 4-5 sentences
- Formal greeting + sign-off structure

## Step 3 — Originality check

Flag if content:
- Could be written by anyone with a search engine
- Contains no firsthand experience or specific evidence
- Uses recycled industry framing
- Has no "only I could write this" quality
- Uses generic examples instead of specific ones

## Step 4 — Score

### Blog and LinkedIn

| Dimension | Target |
|-----------|--------|
| AI-Likeness (lower = better) | 1-3 |
| Authenticity | 8-10 |
| Reader Value | 7-10 |
| Domain Credibility | 7-10 |

### Email

| Dimension | Target |
|-----------|--------|
| AI-Likeness (lower = better) | 1-3 |
| Authenticity | 8-10 |
| Clarity | 8-10 |
| Appropriate Tone | 8-10 |

### Slack

| Dimension | Target |
|-----------|--------|
| AI-Likeness (lower = better) | 1-2 |
| Naturalness | 8-10 |
| Clarity | 8-10 |
| Brevity | 8-10 |

One-sentence justification per score.

If AI-Likeness is low but value/credibility/clarity is
also low: call it out explicitly. Clean but hollow.

## Step 5 — Review report

Skip this step in direct output mode unless
output-validator specifically requests the report.

```
## [Content Type] Review

**Detected as:** [type]
**Voice calibration:** [from VOICE-AND-STYLE.md or generic]

### Overall Assessment
[2-3 sentences]

### Scores
| Dimension | Score | Note |
|-----------|-------|------|
| AI-Likeness | X/10 | |
| [Dim 2] | X/10 | |
| [Dim 3] | X/10 | |
| [Dim 4] | X/10 | |

### AI Pattern Flags
[Every flagged phrase/structure with exact quote]

### Originality Flags
[Every concern]

### Top 3 Changes
1.
2.
3.
```

## Step 6 — Rewrite

Universal rules:
- Never add ideas not in the original
- Never remove substance — only change delivery
- Replace every flagged AI phrase with natural language
- Vary sentence length
- Replace generic openings with specific hook
- Replace summary closings with challenge or principle
- Break uniform paragraph rhythm
- Apply voice profile from VOICE-AND-STYLE.md
- If concrete example missing: add placeholder
  [ADD SPECIFIC EXAMPLE FROM YOUR EXPERIENCE]

LinkedIn rewrites:
- Keep under 1,300 or 3,000 characters
- 1-3 hashtags woven naturally or dropped
- Remove engagement bait closers
- Replace arrow chains with real sentences
- Replace one-line-per-paragraph with real paragraphs

Email rewrites:
- Lead with the ask, not context
- Cut to minimum length
- Specific CTA
- One ask only, one sign-off only

Slack rewrites:
- Maximum 4-5 sentences
- Lead with ask or action item
- No formal greeting or sign-off

**Draft review mode closing:**
"Your edits on top of this are often the best version."

**Direct output mode:**
Deliver clean rewritten content only. No closing line.

## Step 7 — Skill self-update

After every review, automatically:
1. Compare flags raised against existing detection lists
2. If a new pattern emerged not already documented:
   - Write as a specific, flaggable rule with example
   - Add to the correct section
   - Only if you can give a concrete example

Output to user:
```
## Skill Update
- [X] new pattern(s) added: [list]
- [ ] no new patterns this review
```
