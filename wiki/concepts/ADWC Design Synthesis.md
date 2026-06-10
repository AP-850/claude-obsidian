---
type: concept
title: "ADWC Design Synthesis"
created: 2026-05-26
updated: 2026-05-26
tags:
  - sbtdws
  - adwc
  - design
  - synthesis
  - ctvmr
  - teiw
  - dww
status: developing
related:
  - "[[ADWC Three Wing Structure]]"
  - "[[ADWC Transformation Concept]]"
  - "[[CTC-L JTW Reference Model]]"
  - "[[SBTDWS Overview]]"
  - "[[SBTDWS 9 Directed Tasks]]"
  - "[[SBTDWS 2030 Timeline]]"
  - "[[Three Development Thematics]]"
  - "[[SBTDWS CAPDEV Projects]]"
  - "[[SBTDWS Key Relationships]]"
  - "[[ATI-Hub Concept]]"
  - "[[PGIC Concept]]"
  - "[[SBTDWS PM Framework]]"
  - "[[Rapid Innovation FPV Pilot]]"
  - "[[Capability Gap Experimentation Platform]]"
  - "[[sbtdws/_index]]"
sources:
  - "[[sbtdws-chatgpt-transfer]]"
  - "[[research-ctc-l-jtw-australia]]"
  - "[[build-capability-gap-platform]]"
---

# ADWC Design Synthesis

A synthesized design concept for the All Domain Warfare Centre, derived from four ingested source sessions (ChatGPT transfer, Australian CTC-L/JTW research, GAP-X platform build) and the existing SBTDWS wiki domain.

Navigation: [[sbtdws/_index]] | [[ADWC Three Wing Structure]] | [[ADWC Transformation Concept]]

---

## The Central Argument

ADWC is not a training school that also does experimentation. It is a **readiness certification authority** that is fed by a training school and informed by an experimentation cell.

That inversion is the design. Everything else follows from it.

The output ADWC produces is not courses completed. It is a certification verdict: this formation can prosecute All Domain Warfare in a desert environment, or it cannot.

---

## Three Components, One Purpose

```
┌─────────────────────────────────────────────────────────┐
│              ADWC: Desert Readiness Engine              │
│                                                         │
│  ┌──────────────┐   feeds    ┌──────────────────────┐  │
│  │     DWW      │ ─────────► │    CTVMR Wing        │  │
│  │ Desert       │            │  Collective Training  │  │
│  │ Warfare Wing │            │  Validation           │  │
│  │ (feeder)     │            │  Mission Rehearsal    │  │
│  └──────────────┘            │  ── MAIN EFFORT ──   │  │
│                              └──────────┬───────────┘  │
│  ┌──────────────┐   informs            │               │
│  │    TEIW      │ ◄──────────── lessons│               │
│  │ Tactical     │ ─────────── doctrine►│               │
│  │ Experiment-  │            (narrow   │               │
│  │ ation Wing   │             charter) │               │
│  └──────────────┘                      │               │
│                              ▼ certifies                │
│                    [ PG Unit: Ready / Not Ready ]       │
└─────────────────────────────────────────────────────────┘
```

---

## Component 1 — Desert Warfare Wing (DWW)

**Role: The feeder. Not the identity.**

Individual and environmental specialist training. Everything SBTDWS does today in its Individual Skills Wing, largely unchanged. Light UxS and multi-domain enhancements woven into existing courses — replacement lesson content, not new courses:

- Desert driving: add UGV cooperation, signature reduction, autonomous vehicle safety
- Patrolling: add counter-drone awareness, sensor avoidance
- SERE / desert skills: add dispersed sustainment, autonomous resupply concepts

Maximum impact, minimum workload change.

**The cultural task is harder than the structural one.** DWW is transitioning *within* the same enterprise — not geographically separate like JTW was from CTC-L (see [[CTC-L JTW Reference Model]]). The message must be made explicit and repeated: DWW success is measured by how well CTVMR performs, not by DWW throughput. This must come from the Commandant, not from an org chart.

---

## Component 2 — CTVMR Wing

**Role: The main effort. The identity of ADWC.**

Collective Training, Validation, and Mission Rehearsal. Three pillars, all non-negotiable, all interdependent. A weakness in any one degrades the other two.

### Pillar 1 — OPFOR

Not borrowed. Not a role-player pool with insufficient authority. Dedicated, persistent, resourced to win. Equipped with FPV, EW, deception assets, and hybrid threat behaviours. A weak OPFOR is worse than no OPFOR — it teaches the wrong lessons and confirms existing behaviour rather than exposing gaps.

### Pillar 2 — OC/T Cadre

The most important near-term decision in the entire design. The human element that converts exercise events into corrective insight. Must be accredited, empowered, and — critically — given the **authority to fail**. An OC/T cadre without that authority is an audience, not an evaluator.

The E&E Wing retraining is the vehicle. Q2 27 IOC is the gate. Every month of delay on this decision compounds into the MLOC gate. Start now.

### Pillar 3 — AAR Process

Structured, rigorous, non-punitive. Every collective serial ends with an AAR that feeds the lessons register, which feeds TEIW. Without this, the learning loop breaks. AAR is not optional and not abbreviated.

### Mission Rehearsal Sub-Function

ADWC's Mission Rehearsal function *exceeds* the Australian CTC-L model — it draws closer to the NTC/JRTC pre-deployment MRX construct. This must be preserved as a **distinct design requirement**, not collapsed into general collective training. It requires its own EXCON/HICON capability, scenario design cell, and eventually Hameem infrastructure (IOC Q4 28). It is the function that makes ADWC indispensable to J7.

### The Three Thematics Run Through CTVMR

[[Three Development Thematics]] (Experimentation to Adaptation, UxS Tactical Employment, IW/UW) are not separate programs sitting alongside CTVMR. They are the *content* of CTVMR exercises. By 2028 these are what CTVMR exercises look like — themed, doctrine-generating, and publicly showcased.

---

## Component 3 — TEIW

**Role: The learning loop. Deliberately narrow.**

Genuinely novel — the Australians gesture toward this in CTC 2025 Concept but have not formalised it. The biggest risk is scope creep absorbing CTVMR resources before the main effort is mature.

**The charter must be written before the wing stands up, and it must be narrow:**
- Connected to FDC 5 / J3 WDC governance only
- Problem statements come from CTVMR AAR outputs and operational units — not from TEIW itself
- Makhlab 1 is the first bounded sprint
- [[Capability Gap Experimentation Platform]] (GAP-X) governs every trial: no trial without a hypothesis, data collection plan, and decision gate

**What TEIW does:** Converts observed gaps into tested TTPs and doctrine recommendations. Feeds back into CTVMR exercises.

**What TEIW does not do:** Procure equipment. Run its own innovation programme. Set its own problem statements. It is the field execution node — J3 WDC sets direction; PGIC/ATI-Hub is the eventual handover destination for anything that graduates beyond tactical experimentation.

**The loop:** CTVMR runs an exercise → AAR surfaces a gap → TEIW opens a GAP-X case → hypothesis designed → sprint conducted → TTP output feeds back into CTVMR. The loop closes.

---

## The Governance Skeleton

| Layer | Tool | Governs |
|-------|------|---------|
| Doctrine and Training Authority (SAT Cell evolved) | Standards docs, accreditation | OT standards, ADW competency profiles, course design |
| GAP-X (`gap-x-prototype.html`) | Case-based governance | Every TEIW trial: intake → market → experiment → TTP → decision |
| SBTDWS PM Master (`SBTDWS_PM_Master.xlsx`) | LOE tracking, Gantt, dashboard | The transformation programme across 6 LOEs and 80 items |

These are two distinct governance layers for two distinct things. Do not conflate them.

---

## The Sequencing

The sources lay out a timeline but don't make sequencing priority explicit.

**Do first — before anything else:**
1. Start OC/T cadre development
2. Sign the Force Generation Pipeline ToR (J3/J7/SBTDWS)

Neither requires structural reorganisation, capital, or external approvals that aren't available now. Both unlock everything downstream.

**Do second:**
Run the FPV Pilot (STC + SBTDWS + Hameem Fund). Three partners, bounded cost, one prototype. This proves the [[Rapid Innovation FPV Pilot]] model before PGIC is funded and builds command credibility for the larger ATI-Hub ask.

**Do third:**
Structural reorganisation (Q4 26) — only after the 6GW training review is complete. Announce DWW / CTVMR / TEIW. Communicate the identity shift deliberately.

**Don't do yet:**
Hameem capital. PGIC stand-up. ADWC full rebrand. These are Phase 2/3 activities. Attempting them before CTVMR is credible is the "ambition before credibility" failure mode explicitly warned against in the sources.

---

## The One Design Recommendation Not in Any Source

**Name the first fully validated formation. Make it public.**

Put the Commandant in front of the unit commander and say: "This formation is validated ready for All Domain Warfare operations in a desert environment."

That moment is when ADWC becomes real — not when the org chart changes, not when Hameem is built, not when the EMAD brief is approved. The first validated formation is the proof of concept for the entire design. Everything before it is preparation. Everything after it is scale.

---

## Design Risks

| Risk | Nature | Mitigation |
|------|--------|-----------|
| TEIW scope creep | Hardest to control; most likely failure mode | Write the narrow charter before the wing stands up |
| OC/T cadre delay | Every month delays MLOC gate | Start now; this is a sequencing decision, not a resourcing decision |
| DWW identity crisis | Underestimated cultural risk | Commandant must communicate the repositioning explicitly and repeatedly |
| ADWC name vs domain access | Name promises 6 domains; SBTDWS has 2 | Address before 2028 public-facing showcase year |
| O5 resistance | Mid-management inflection point | Deliberate O6 CoC engagement alongside structural announcement |

---

## Design Summary

| Element | Design choice |
|---------|--------------|
| Identity of ADWC | CTVMR Wing — the readiness certifier |
| DWW | Feeder — repositioned, not diminished |
| TEIW | Narrow charter, tied to FDC 5/J3 WDC only |
| ATI-Hub/PGIC | Future partner — not yet part of ADWC structure |
| Three thematics | Content of CTVMR exercises — not separate programs |
| OC/T cadre | Start now — longest lead time in the design |
| FPV Pilot | First proof of concept — run before PGIC is funded |
| Mission Rehearsal | Distinct sub-function — must not be collapsed into CTW |
| First milestone that matters | First validated formation — this is when ADWC becomes real |
