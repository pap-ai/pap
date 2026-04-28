---
name: agent-directory
description: Routing reference for which agent handles
  which type of task. Loaded when task type is unclear.
  Internal use only.
triggers:
  - "which agent"
  - "who handles"
  - ambiguous task routing
model: claude-haiku-4-5
---

# Agent Directory

Internal routing reference. Never referenced by name to users.

## System agents

**dispatcher** — first responder, routes all messages
**steward** — weekly synthesis, Monday 8am, cross-workspace
**security** — quarantine, drift scan, threat monitoring
**curiosity** — intake interviews, new features (called internally)
**scaffolder** — workspace creation (Moment 1 only)
**executor** — go-live orchestration, Definition of Done
**validator** — system health checks, preference validation
**help** — user questions, #help #feedback #preferences
**cost-monitor** — usage analysis, subscription guidance
**performance-monitor** — mistake patterns, quality signals
**connector** — second brain processing, connection finding
**synthesizer** — knowledge synthesis from second brain
**[workspace]-agent** — primary agent per workspace

## Routing by channel

#general: greeting → respond warmly; substantive → curiosity;
  question → help; workspace status → workspace agent
#new-workspace: always curiosity
#capture: always connector (with security pre-check)
#[workspace]: all messages → workspace's primary agent
#help #feedback #preferences: always help
#daily-briefing #pap-status #notify: read-only, help if user posts
#uninstall: static card only

## Intent signals

Curiosity: "I want to", "can we", "what if", "new idea",
  "I've been thinking", "is it possible"
Help: "how do I", "where is", "what is", "confused by",
  "something went wrong", "not working"
Steward: "across all workspaces", "system health",
  "what's the status of everything"
Synthesis: "what do I think about", "summarize my thinking",
  "based on everything I've captured"

Ambiguous → help. Help re-routes if needed.
Never leave a message unrouted.
