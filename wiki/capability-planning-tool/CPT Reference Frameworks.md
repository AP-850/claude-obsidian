---
type: reference
title: "CPT Reference Frameworks"
created: 2026-06-12
updated: 2026-06-12
tags:
  - capability-planning
  - dotmlpf
  - solution-types
  - maturity
  - frameworks
status: active
related:
  - "[[CPT Overview]]"
  - "[[CPT Architecture]]"
  - "[[CPT Framework Research]]"
  - "[[capability-planning-tool/_index]]"
---

# CPT Reference Frameworks

Navigation: [[capability-planning-tool/_index]] | [[CPT Overview]] | [[CPT Architecture]]

The fixed frameworks built into the tool. These are not configurable — they encode the planning logic.

---

## DOTMLPF Dimensions

Used to classify the root cause of every capability gap. Prevents planners from treating every problem as an equipment problem.

| Code | Full Name | What It Covers | Example Gap |
|------|-----------|----------------|-------------|
| D | Doctrine | Principles, guidance, how the org operates | No doctrine exists for multi-domain entry operations |
| O | Organisation | Structure, command relationships, force design | No dedicated ISR unit; capability is fragmented |
| T | Training | Individual and collective training standards | Units cannot integrate fires with manoeuvre at brigade level |
| M | Materiel | Equipment, platforms, systems, supplies | No organic counter-UAS system below battalion |
| L | Leadership and Education | Leader development, professional education | Commanders lack understanding of EW capabilities |
| P | Personnel | Availability of qualified people; manpower | Insufficient qualified signals operators |
| F | Facilities | Infrastructure, ranges, installations | No simulation facility for CBRN training |
| Po | Policy | Governing rules, authorities, legal constraints | Policy prevents use of certain ISR systems domestically |

> Rule of thumb: if the gap would persist even after buying new equipment, it is not a Materiel gap.

---

## Solution Type Decision Logic

```
Can the gap be closed by the unit itself?
    YES ──► ORGANIC
            (Developed and held within the unit)
    
    NO ──► Can another internal team/unit provide it?
               YES ──► SHARED
                        (Cross-team or cross-unit support arrangement)
               
               NO ──► Does closing it require a higher authority
                       decision, resource, or external body?
                           YES ──► ESCALATED
                                    (Requires higher authority or external organisation)
                           
                           NO ──► Can a contractor or external partner deliver it?
                                       YES ──► CONTRACTED
                                                (External partner or contractor)
                                       
                                       NO ──► ACCEPTED RISK
                                               (Gap acknowledged; not currently resourced)
                                               (Document rationale required)
```

**Principle:** Work inward-out. Always exhaust internal organic options first, then internal shared options, before escalating or contracting. Accepted Risk is a last resort requiring explicit documentation — not a default.

---

## Maturity Scale

Applied to both current maturity and target maturity for each gap.

| Level | Label | Description |
|-------|-------|-------------|
| 1 | None | Capability does not exist |
| 2 | Initial | Ad hoc; relies on individuals; not repeatable |
| 3 | Developing | Some process exists; partially repeatable |
| 4 | Capable | Defined, documented, and consistently delivered |
| 5 | Advanced | Optimised; continuously improved; exportable |

> The gap between Current Maturity and Target Maturity defines the transformation requirement. A gap from 2→4 is different in scale and nature from a gap from 1→5.

---

## Severity Scale

| Level | Label | Planning Implication |
|-------|-------|---------------------|
| 1 | Minor | Can be tolerated; low priority |
| 2 | Low | Should be addressed but not urgent |
| 3 | Moderate | Affects mission delivery; medium priority |
| 4 | High | Significantly degrades mission capability |
| 5 | Critical | Mission cannot be achieved without resolution |

> Critical and High severity gaps drive prioritisation in the Action Plan. Accepted Risk solutions for Critical gaps must be explicitly flagged to leadership.
