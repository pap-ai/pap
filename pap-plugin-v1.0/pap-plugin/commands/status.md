---
name: status
description: Get current status of PAP or a specific workspace.
syntax: /status [optional workspace name]
---

# /status

Without argument: overall PAP status, scheduled
tasks for today, any open improvements.

With workspace name: that workspace's status,
last run, next run, recent outputs.

Routes to:
- Help agent (no argument)
- Workspace agent (specific workspace)
