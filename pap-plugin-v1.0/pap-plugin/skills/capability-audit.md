---
name: capability-audit
description: Inventories available capabilities before
  any new workspace starts. Identifies gaps and drafts
  missing agents. Auto-fires at start of every curiosity
  interview and start of every Build-Measure-Learn loop.
triggers:
  - new workspace creation
  - start of BML loop
  - "what can we build"
model: claude-haiku-4-5
---

# Capability Audit

Before building anything new, know what already exists.

## What this skill does

Reads the user's environment to produce a snapshot:
- Plugin agents and skills
- Workspace-specific agents
- Authorized connectors from CONFIG.md
- Computer Use authorization status
- Claude in Chrome authorization status
- External services with PAP Vault credentials
- Active scheduled tasks
- Available APIs and tokens

## Output format

```
CAPABILITIES AVAILABLE FOR THIS WORKSPACE

Active connectors:
✓ [connector] — [what it does]

Authorized capabilities:
✓ Computer Use ([trust level])
✓ Claude in Chrome

Existing agents that might apply:
✓ [agent] — [what it does]

External services with vault access:
✓ [service] — [authorized scope]

Gaps for this project:
✗ [missing capability] — needed for [reason]
  Draft agent created: [name]-draft.md
```

## Gap handling

For each gap:
Auto-draft a starter agent file with correct frontmatter
and system prompt based on project needs.

Mark draft: add this header to system prompt:
```
DRAFT — NOT ACTIVE
Created by capability-audit. Will not be invoked until
approved. To activate: approve in Discord or rename
to remove "-draft" suffix.
```

Notify user after workspace welcome message:
"I've created a draft [agent name] agent for specialized
tasks this workspace will need. It's ready when you are."

No user approval needed for creation — the workspace
was approved, covering its agents.

## When to skip the audit

The audit always runs. The calling agent decides
whether to use the output.

For trivial requests: quick output, minimal gaps.
For substantial work: full output drives the conversation.
