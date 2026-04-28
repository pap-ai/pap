---
name: bml-memory-checkpoint
description: Writes validated learnings to durable
  storage at end of each Build-Measure-Learn loop.
  Auto-fires when a loop completes.
triggers:
  - end of BML loop
  - assumption resolved
  - prototype tested and result captured
model: claude-haiku-4-5
---

# Build-Measure-Learn Memory Checkpoint

At the end of every loop, write what was learned
to durable storage. Don't rely on conversation
context to remember.

## When this fires

After every prototype, regardless of outcome.
At workspace state changes (design → live, live → paused).

## What gets written

**LEARNINGS.md** (appended):
```
## Loop [N] — [date]
Tested: [assumption(s)]
Outcome: [passed / failed / partial]
Evidence: [what demonstrated this]
Surprise: [anything unexpected]
Implication: [what this means for next steps]
```

**ASSUMPTIONS.md** (updated):
- Tested assumptions: status updated (✓ or ✗)
- New assumptions: added with risk color
- Deferred: noted as such

**DECISIONS.md** (appended with any decisions made):
```
## [date] — [decision]
Context: [why this came up]
Decision: [what was decided]
Rationale: [why]
Alternatives: [if any]
```

**QMD collection** receives validated learnings as
searchable entries with cross-workspace tags.

## Track user-added assumptions

Any assumption the user adds during a loop is tagged
as "user-added" in ASSUMPTIONS.md.
Steward reviews these weekly across workspaces.
If same type keeps appearing: flags for curiosity agent
to include in standard mapping.

## Why this matters

Thread context is ephemeral.
LEARNINGS.md is the durable memory.
If it's not in LEARNINGS.md, it didn't happen.
