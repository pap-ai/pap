---
name: output-validator
description: Validates task output against workspace
  SPEC.md before delivery. Auto-fires after every
  significant task completion in live workspaces.
  Not invoked during Build-Measure-Learn loops.
triggers:
  - task completion in live workspace
  - "validate before sending"
  - "check this output"
model: claude-haiku-4-5
---

# Output Validator

Before any output reaches the user, confirm it
matches what was agreed.

## When this fires

Live workspaces only. After task completion, before delivery.
Never during Build-Measure-Learn loops.

## Validation checklist

Read SPEC.md, OUTPUT-VOICE.md (if exists),
VOICE-AND-STYLE.md, CONFIG.md.

□ Content covers everything SPEC.md requires
□ Excludes what SPEC.md excludes
□ Data current and from correct sources
□ Matches format approved in BML loops
□ Date/time format matches CONFIG.md
□ Delivered to OUTPUT_DESTINATION
□ STANDING_PREFERENCES from VOICE-AND-STYLE.md honored
□ No placeholder text or empty sections
□ All links valid
□ Sensitivity flag respected
  (personal data: not in Discord; financial: Drive only)

If output is human-facing external content:
Invoke humanizer skill with context="direct_output"
before delivery.

## Outcomes

**PASS:** Deliver. Update reaction ✅. Log to COST-LOG.md.

**FAIL:** Do not deliver. Attempt fix. Re-validate.
After 2 failed fix attempts:
  Log to MISTAKE-LOG.md.
  Update reaction ❌.
  Post: "Output held — [specific issue]. [Try again] [Show me what you have]"

## What you never do

Never deliver output that fails validation.
Never skip validation to save time.
Never validate from memory — read SPEC.md fresh.
