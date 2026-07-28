---
type: reference
title: "CPT Outputs and Design"
created: 2026-06-12
updated: 2026-06-12
tags:
  - capability-planning
  - outputs
  - design
  - tool
status: active
related:
  - "[[CPT Overview]]"
  - "[[CPT Architecture]]"
  - "[[capability-planning-tool/_index]]"
---

# CPT Outputs and Design Decisions

Navigation: [[capability-planning-tool/_index]] | [[CPT Overview]] | [[CPT Architecture]]

---

## Primary Outputs

| Output | Description |
|--------|-------------|
| Capability Gap Register | All gaps with mission, unit, domain, DOTMLPF dimension, severity, current/target maturity |
| Dependency Matrix | m×n grid of unit-to-unit support relationships with status |
| Solution Register | All gaps with assigned solution type, owner, timeline, and rationale |
| Sequenced Action Plan | Phased table: owner, timeline, resources, metric, solution type |

## Visual Outputs

| Output | Description |
|--------|-------------|
| Capability Heat Map | Domain × average severity; colour-coded from none to critical |
| Solution Breakdown | Bar chart of solution type distribution |
| Maturity Gap View | Current vs target maturity per gap (colour-coded dots) |
| Dependency Matrix | Visual grid: established/partial/gap/proposed relationships |

## Planning Metrics (Summary Dashboard)

- Validated missions count
- Total capability gaps
- Critical gaps (severity 4 or 5)
- Total action items
- Gaps resolved organically vs escalated vs accepted as risk
- Actions by phase and priority

---

## Design Decisions and Rationale

**Why DOTMLPF and not a simpler classification?**
DOTMLPF is the most rigorous and widely validated framework for classifying capability gaps. Its eight dimensions are specifically designed to stop planners treating every problem as an equipment problem. Used by US, UK, NATO, and allied forces at scale. For a commercial context, the same dimensions apply — substitute "doctrine" for "operating procedures" and "materiel" for "systems/technology."

**Why five solution types and not three?**
The five types (Organic / Shared / Escalated / Contracted / Accepted Risk) map directly onto the decision logic planners actually face. Three types would conflate "we can get a partner to do this" with "we need HQ approval and funding" — which are fundamentally different escalation paths with different timelines, authorities, and risks.

**Why is the action plan gated?**
The most common failure mode in transformation planning is producing an activity list and calling it a plan. Gating the action plan behind mission validation, gap identification, and solution development forces planners to earn the action plan through upstream thinking.

**Why are phases user-defined?**
Different organisations use different temporal frameworks (fiscal years, programme phases, calendar years, near/mid/far term). Forcing a specific phase structure would reduce configurability without adding planning value.

**Why is dependency mapping optional?**
Not all organisations have meaningful inter-unit dependencies to map, particularly smaller or single-unit deployments. Making it optional preserves universal applicability. Users who skip it miss the cross-unit dependency visibility but are not blocked.

---

## Future Extensions

| Module | Priority | Description |
|--------|----------|-------------|
| Force Design Review | High | Structured trade-off decision capture — what to consolidate, deprioritise, or repurpose; explicit billpayer decisions |
| Sync Matrix | High | Visual calendar/timeline view of actions against milestones and phases |
| Risk Register | Medium | Formal risk log linked to accepted-risk gaps; likelihood × impact scoring |
| Progress Tracking | Medium | RAG status updates against action items over time; completion tracking |
| Export | Medium | PDF/DOCX generation of full planning output for briefings |
| Multi-Org / Coalition | Low | Cross-organisation planning where gaps span multiple entities |
| Scenario Library | Low | Pre-loaded mission scenario templates for common planning contexts |
| Weighted Prioritisation | Low | Analytical Hierarchy Process (AHP) scoring to rank gap priorities across competing criteria |
