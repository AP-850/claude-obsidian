---
type: reference
title: "CPT Framework Research"
created: 2026-06-12
updated: 2026-06-12
tags:
  - capability-planning
  - frameworks
  - dotmlpf
  - nato
  - togaf
  - research
status: active
related:
  - "[[CPT Overview]]"
  - "[[CPT Reference Frameworks]]"
  - "[[capability-planning-tool/_index]]"
---

# CPT Framework Research

Navigation: [[capability-planning-tool/_index]] | [[CPT Overview]] | [[CPT Reference Frameworks]]

Six frameworks researched and synthesised into the tool's design. Research conducted June 2025.

---

## Military and Defence Frameworks

### Capabilities-Based Planning (CBP)
**Origin:** US Department of Defense, 2001 Quadrennial Defense Review.

Shifts from threat-based to capability-based planning. Top-down: starts from mission/policy and cascades to capability requirements.

**Process:** Policy guidance → model future environment → identify required capabilities → identify gaps → develop solutions.

**Contribution to CPT:** Mission-first cascade logic; top-down design philosophy; scenario-based gap identification.

**Limitation:** Relies on classified threat models; not easily transferred to a generic tool without specialist support.

---

### DOTMLPF / DOTMLPF-P
**Origin:** US Joint Chiefs of Staff; embedded in JCIDS.

Eight-dimensional framework classifying capability gaps and their solutions. Prevents organisations defaulting to equipment procurement when the gap may be in doctrine, training, or leadership.

| Code | Dimension | Covers |
|------|-----------|--------|
| D | Doctrine | How the organisation operates; principles and guidance |
| O | Organisation | Structure, command relationships, force design |
| T | Training | Individual and collective training standards |
| M | Materiel | Equipment, platforms, systems, supplies |
| L | Leadership and Education | Leader development, professional education |
| P | Personnel | Availability of qualified people; manpower |
| F | Facilities | Infrastructure, ranges, installations |
| Po | Policy | Governing rules, authorities, legal constraints |

Key insight: a deficiency in any one dimension adversely impacts the whole capability.

**Contribution to CPT:** Eight-dimensional gap classification built into the gap analysis module; forces consideration of non-material solutions before procurement.

---

### JCIDS — Capabilities-Based Assessment (CBA)
**Origin:** US Joint Capabilities Integration and Development System.

Three-phase assessment process:

| Phase | Name | What it does |
|-------|------|-------------|
| 1 | Functional Area Analysis (FAA) | Identifies operational tasks, conditions, and standards needed to accomplish objectives |
| 2 | Functional Needs Analysis (FNA) | Assesses whether current and programmed capabilities can accomplish those tasks; outputs list of gaps |
| 3 | Functional Solutions Analysis (FSA) | Evaluates DOTMLPF solutions for each gap; distinguishes material vs non-material approaches |

The FSA explicitly asks: can this gap be solved without buying new equipment? Only after exhausting non-material options is a material solution recommended.

**Contribution to CPT:** FAA → FNA → FSA as the core three-phase gap analysis workflow; clear separation of identifying gaps from proposing solutions; escalation logic (non-material first, material second, external acquisition last).

**Limitation:** Addresses reported gaps rather than anticipating future gaps; consensus-heavy and slow by design.

---

### NATO Defence Planning Process (NDPP)
**Origin:** NATO.

Five-step, four-year planning cycle:

1. Establish Political Guidance
2. Determine Requirements → Gap Analysis (Shortfalls / Surplus / To be maintained) → Shortfall Prioritisation
3. Apportion Requirements and Set Targets
4. Facilitate Implementation (continuous)
5. Review Results

Key insight: the gap analysis step produces three categories — shortfalls, surplus, and maintained — not just a list of problems. Shortfall prioritisation is a structured output, not an afterthought.

**Contribution to CPT:** Shortfall/surplus/maintained classification; multi-tier allocation logic (internal → shared → external); long-range (20-year) planning horizon demonstrates the importance of strategic framing over tactical activity.

---

## Enterprise Architecture Frameworks

### TOGAF — The Open Group Architecture Framework

Eight-phase Architecture Development Method (ADM). Relevant phases:
- **Phase A:** Architecture Vision — define scope and capability objectives
- **Phase B:** Business Architecture — capability map, gap analysis, heat mapping
- **Phase E:** Opportunities and Solutions — capability roadmap
- **Phase F:** Migration Planning — sequence the transition from current to target state

Capability heat mapping (Phase B): capabilities plotted on a heat map showing maturity (current vs target), effectiveness, performance, and value.

Four maturity dimensions: People, Process, Technology, Information.

**Contribution to CPT:** Capability heat map as primary visual output (domain x severity); current vs target maturity as the core gap measurement; "build, buy, improve, or retire" taxonomy adapted to organic/shared/escalated/contracted/accepted.

Key insight: because capabilities change slowly while processes and technologies change frequently, they provide a durable planning framework — plan around WHAT the organisation needs to do, then determine HOW.

---

### Business Capability Mapping (BCM)

Hierarchical capability decomposition (Level 1 → Level 2 → Level 3) with capability-to-capability dependency mapping. Each capability assessed for whether it drives or is driven by every other — revealing which are foundational (build first) and which are dependent.

**Contribution to CPT:** Hierarchical decomposition scales from strategic to tactical; dependency matrix structure; heat map and capability roadmap as the standard output pair.

---

## Commercial Transformation Frameworks

### McKinsey 7S Framework

Seven interdependent elements: Strategy, Structure, Systems, Shared Values, Skills, Style, Staff.

Relevance: capability gaps are never just about equipment or training. They reflect misalignments across structure, leadership culture, systems, and people simultaneously.

**Contribution to CPT:** The DOTMLPF dimension tagging serves a similar function — forcing users to identify which dimension the gap sits in, not just what the gap is.

---

## Framework Synthesis Table

| Framework | Origin | Best Contribution |
|-----------|--------|------------------|
| CBP | US DoD | Mission-first logic; top-down cascade from goal → capability → gap |
| DOTMLPF | US Joint Chiefs | Eight-dimensional gap classification; prevents equipment-only thinking |
| JCIDS / CBA | US JCIDS | FAA → FNA → FSA workflow; separates gap identification from solution development |
| NATO NDPP | NATO | Shortfall/surplus/maintained; tiered allocation (internal/shared/external) |
| TOGAF / BCM | Open Group | Capability heat mapping; current vs target maturity; dependency mapping |
| McKinsey 7S | McKinsey | Gaps live across structure, people, culture — not just materiel |

---

## Critical Gaps in Existing Tools

Five weaknesses appearing consistently across all frameworks — where CPT goes further:

**Gap 1 — Dependencies and support relationships are poorly handled.**
Architecture frameworks and CBP processes are not linked intuitively. This tool makes cross-unit dependency mapping accessible, not expert-dependent.

**Gap 2 — Most tools default to acquisition, not transformation.**
JCIDS, DOTMLPF, and TOGAF all tend to funnel users toward procurement. CPT has an explicit non-material solution pathway that exhausts internal options before escalating.

**Gap 3 — Force design trade-off decisions are not supported.**
Existing tools identify gaps and propose solutions, but none help leaders decide what to deprioritise, consolidate, or accept as risk. CPT includes "Accepted Risk" as a formal solution type requiring documented rationale.

**Gap 4 — The action plan is treated as the starting point, not the output.**
Most tools jump to action before the capability logic is established. CPT enforces the correct sequence through module gating.

**Gap 5 — Escalation pathways are implicit, not structured.**
No existing tool provides a clean, configurable decision tree for when a gap should be solved organically, shared, escalated, outsourced, or accepted as risk. CPT's solution module makes this explicit and required.
