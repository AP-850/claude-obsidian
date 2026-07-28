---
type: concept
title: "CPT Overview"
created: 2026-06-12
updated: 2026-06-12
tags:
  - capability-planning
  - tool
  - planning-logic
status: active
related:
  - "[[capability-planning-tool/_index]]"
  - "[[CPT Architecture]]"
  - "[[CPT Framework Research]]"
  - "[[sources/capability-planning-tool-project]]"
---

# Capability Planning Tool — Overview

Navigation: [[capability-planning-tool/_index]] | [[CPT Architecture]] | [[CPT Framework Research]]

An organisation-agnostic, capability-led planning tool that enforces the correct planning sequence. Applicable to military, government, or corporate transformation planning. v1 built as a React application.

---

## What the Tool Is

A structured thinking environment that forces the right questions in the right order. It produces an action plan as the output of upstream logic — not as the starting point.

**What it IS:**
- A structured thinking environment that forces the right questions in the right order
- A capability gap register linked to missions and solutions
- A dependency mapper that reveals whether gaps can be closed internally or require escalation
- An action plan generator that earns its outputs through upstream logic

**What it is NOT:**
- A project management tool
- A task tracker
- A calendar or sync matrix builder
- A way to quickly generate an action plan

---

## The Planning Problem

Most transformation planning starts in the wrong place. Organisations move straight to a calendar, a training schedule, or an equipment wish-list — and call it a plan.

Tactical activity planning is not transformation. Improving a course, running an exercise, or buying equipment are business-as-usual activities. They do not constitute a capability transformation unless derived from deliberate analysis of:

1. What the organisation must be able to do (missions)
2. What it cannot currently do (capability gaps)
3. Why it cannot do it (DOTMLPF root cause)
4. Who can help (dependencies and support relationships)
5. How to close the gap (solution type)
6. What structural trade-offs are required (force design decisions)
7. What must happen, in what order, owned by whom (action plan)

**The action plan is the last step, not the first.**

---

## The Core Planning Logic

```
MISSION FIRST → CAPABILITY SECOND → STRUCTURE THIRD → SUPPORT FOURTH → ACTION PLAN LAST
```

```
Validate Missions / Goals
        ↓
Identify Capability Gaps (per mission, per unit, by DOTMLPF dimension)
        ↓
Map Dependencies (who supports whom; what is established vs gap)
        ↓
Develop Solution Options (organic / shared / escalated / contracted / accepted)
        ↓
Confirm Force Design Direction (trade-offs, consolidations, priorities)
        ↓
Functional Support Planning (what enabling organisations must do)
        ↓
Build the Action Plan, Sync Matrix, Long-Range Calendar
```

Key principle: do not build the calendar first. Build the logic first.

---

## Design Philosophy

Three non-negotiables:

1. **Sequence is enforced** — the logic chain cannot be bypassed; each module gates the next
2. **The action plan is earned** — produced by the tool after upstream thinking is complete, not entered as a starting assumption
3. **Organisation-agnostic** — no military terminology is hardcoded; all labels are configurable

---

## Build Status (as at 2026-06-12)

| Component | Status |
|-----------|--------|
| Architecture | Complete |
| React application (v1) | Built |
| Seven working modules | Complete |
| Storage API persistence | Complete |
| Capability heat map | Complete |
| Dependency matrix | Complete |
| Solution type distribution | Complete |
| Phased action plan | Complete |
| Force Design Review module | Pending |
| Sync Matrix / visual timeline | Pending |
| Export (PDF/DOCX) | Pending |
| Progress Tracking (RAG) | Pending |

Files: `capability-planning-tool.jsx`, `capability-planning-tool-architecture.md`
