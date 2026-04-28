---
name: resume
description: Resume previously paused scheduled tasks.
syntax: /resume [optional workspace name]
---

# /resume

Reactivates paused scheduled tasks.

Without argument: resumes everything that was paused.
With workspace name: resumes that workspace only.

If workspace was auto-paused after 30 days inactive:
runs catch-up logic if applicable, otherwise resumes fresh.
