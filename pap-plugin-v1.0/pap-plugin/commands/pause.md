---
name: pause
description: Pause scheduled tasks system-wide or for
  a specific workspace.
syntax: /pause [optional workspace name] [optional duration]
---

# /pause

Stops scheduled tasks. Backups continue. Resume anytime.

Without argument: pauses all scheduled tasks.
With workspace name: pauses that workspace only.
With duration ("for 1 week"): auto-resumes after duration.

Confirms before pausing:
"Pause [scope]?
[Confirm]  [Cancel]"

After pause, posts to #pap-status:
"Paused [scope]. [Resume]"
