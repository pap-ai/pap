---
name: lean-startup
description: Build-Measure-Learn process for design
  workspaces. Governs all loops from first prototype
  through production. Auto-fires when design workspace
  transitions from intake to development.
triggers:
  - "first prototype"
  - "start building"
  - "test this assumption"
  - design workspace started
model: claude-sonnet-4-6
---

# Build-Measure-Learn Skill

The goal of each loop is not to build.
The goal is to learn.

If conversation can answer the question,
don't build.

## Terminology rule

Never say "BML" with users.
Always "Build-Measure-Learn" in full.
Internal logs and agent communication may use BML.

## Trust the process reminder

At workspace start, remind the user:
"Before we dive in — focus on describing the
problem you want to solve, not the solution
you're already picturing.

If you say 'I need a spreadsheet,' you'll
probably get a spreadsheet. But the right
answer might be a live dashboard, a weekly
email, or a simple alert — something you
hadn't thought to ask for.

And if along the way you still decide you
want a spreadsheet, you'll absolutely get
there."

## Before every loop

Present the current assumption map.
Triage each assumption:

**ANSWER NOW** — user can resolve immediately
→ Ask the question, record answer, mark resolved
→ Never build to answer what conversation can

**VALIDATE BY SHOWING** — needs prototype
→ Determine minimum fidelity needed
→ Build only that fidelity

**VALIDATE BY DOING** — needs real operation
→ Build functional version with real data
→ Run it, measure results

**DEFER** — interesting but not blocking
→ Add to ASSUMPTIONS.md as deferred

Address ANSWER NOW assumptions first.
Only then determine what to build.

## Assumption bundling

Bundle assumptions in a single prototype when:
- They share the same test environment
- You can clearly attribute results to each separately

No limit on how many assumptions a prototype can test.
A survey could tackle 10 assumptions at once.
The goal is learning efficiency.

## Assumption risk colors

🔴 Red — If wrong, the project fails
🟡 Yellow — If wrong, significant rework
🟢 Green — Low risk, reasonable to assume

## Fidelity levels

Choose the lowest fidelity that can answer the question.
Never go backwards — once a fidelity is validated,
build on it. Never re-prototype something already confirmed.

**Sketch** (description, wireframe, text mockup)
When: testing whether the mental model is right
Cost: minutes

**Low fidelity** (manual process, fake data, mockup)
When: testing whether approach works
Cost: less than an hour

**Medium fidelity** (real data, manual trigger)
When: testing whether it holds up in practice
Cost: a few hours

**Production fidelity** (automated, scheduled)
When: validating the complete experience
Cost: full build

At medium and production fidelity, include UI/design
quality as explicit assumptions:
"User finds the interaction clear and pleasant"
"User can navigate this without explanation"
"Output works well on the user's primary device"
"Notification format meets expectations"
"Pinned card format meets expectations"

After each prototype at any fidelity, include a
brief curiosity-style check in the "learn" phase:
→ What felt right about this?
→ What felt awkward?
→ Was anything confusing?
→ Did this look like something you'd actually use?

One or two questions max, buttons where possible.
These are checking, not interrogating.

## Before building each prototype

State explicitly:

"Here's what I'm building and why:
- Fidelity: [level]
- Assumptions tested: [list — can be multiple]
- Success looks like: [criteria]
- Failure looks like: [criteria]
- Estimated time: [estimate]
- Estimated Claude subscription usage: [low/medium/high]
  (low = minimal impact on your monthly allocation,
   high = may use a meaningful portion)"

[Looks right — start building]  [Let me refine this first]

## Presenting prototypes

Show before explaining.
Lead with the output, not the description.

Choose the right presentation method:
→ Text/data result: formatted message in Discord thread
→ Document/report: Drive link with preview
→ Interactive tool: URL (locally hosted or Drive)
→ Visual mockup: image embedded in Discord

The user should never have to work to see the result.
One tap maximum.

Format:
1. Here's what I built: [show it, in the right format]
2. Here's what it tested: [assumptions]
3. Here's what I found: [result for each assumption]
4. Questions for you: [one at a time, genuinely curious,
   as many as needed to understand the user's reaction —
   but never overwhelming; ask, listen, then ask the next]

## Measuring results

After every prototype, capture:
- Which assumptions passed
- Which assumptions failed
- What new assumptions emerged
- What surprised the user
- Whether output format met expectations
- Whether delivery method felt right

Always include: "User finds output sufficient in
function and presentation" — never pre-resolved.
Real output validates real preference.

## Loop decisions

**FAILED ASSUMPTION → new loop**
Build revised prototype.
Note what failure taught.
Never repeat the same approach.
After 3 failed attempts on the same red assumption:
"We've tried [n] approaches and haven't found one
that works. This might mean the assumption is wrong,
or we're testing it the wrong way.
[Pivot — reframe the whole approach]
[Dig deeper — let me ask you some questions]
[Park it — move to a different assumption]"

**PASSED, MORE ASSUMPTIONS → next loop**
Move to next riskiest.
Advance fidelity if appropriate.

**ONLY MINOR ASSUMPTIONS REMAIN → check in**
"These feel low risk. Do any need testing
before we build the full version?"
[Yes, test these]  [No, proceed to production]

**READY TO EXECUTE → convergence check**
Convergence signals (all three required):
1. New assumptions per loop are slowing
2. User is confirming, not surprised
3. User responds with confidence, not hesitation

Quality gate (all required before executor fires):
□ User has seen production-fidelity output
□ User has no remaining improvement feedback
□ Output tested on intended devices (user confirmed)
□ Notification format confirmed
□ Pinned card format confirmed

If convergence signals look good but quality gate
fails: continue at production fidelity until
quality gate passes.

When ready:
"This is looking ready to run automatically.
Want to go live with it?"
[Yes — let's go live]  [One more thing first]

On confirmation: call executor.

## Time boxing

Set during first loop:
"Based on what we're building, I'd suggest
[timeframe] to reach a validated version.
Does that feel right?"

If exceeded: flag immediately.
Present: continue / extend / pivot / abandon.
Never silently exceed the time box.

## What you never do

Never skip fidelity levels without explicit agreement.
Never build production before medium fidelity validated.
Never proceed past failed assumption without revised approach.
Never run loops in live workspaces (use SPEC.md only).
Never build if conversation can answer the question.
Never force mobile testing if user confirmed desktop-only.
