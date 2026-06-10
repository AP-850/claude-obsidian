---
type: concept
title: "Capability Gap Experimentation Platform"
updated: 2026-05-26
tags:
  - sbtdws
  - teiw
  - capdev
  - software
  - experimentation
  - gap-x
status: active
related:
  - "[[ADWC Three Wing Structure]]"
  - "[[SBTDWS CAPDEV Projects]]"
  - "[[ATI-Hub Concept]]"
  - "[[SBTDWS PM Framework]]"
  - "[[sbtdws/_index]]"
---

# Capability Gap Experimentation Platform (GAP-X)

A single-file HTML prototype that governs the end-to-end lifecycle from capability gap identification through tactical experimentation to TTP, CONOPS, or termination decision. Built to reduce paperwork, improve governance, and allow staff to spend more time conducting trials and innovation.

**Deliverable:** `gap-x-prototype.html` — located at `Documents\Claude\Projects\EXCON Pro\`

Navigation: [[sbtdws/_index]] | [[ADWC Three Wing Structure]] | [[ATI-Hub Concept]]

---

## Product Ethos

> Reduce paperwork, improve governance, allow staff to spend more time conducting trials, experimentation, and innovation.

This is the TEIW's governance tool. Every CAPDEV trial, Makhlab 1 sprint, and FDC 5 experiment should flow through a structure like this. It replaces ad hoc reporting with a shared, repeatable case model.

---

## The 7-Stage Workflow

All stages share a single "Case" record — one ID flows from intake to decision.

### Stage 1 — Capability Gap Intake

Captures: operational problem, gap, user need, environment, mission context, urgency, constraints, desired effect.

Auto-classifies using:
- **DLOD / DOTMLPF-P** (dual-labelled: UK/US)
- **TEPIDOIL**
- **POPIT**
- Combat functions (UK) / Joint warfighting functions (US)
- Readiness impact, risk

---

### Stage 2 — Market and Capability Analysis

Deep-dive market analysis of COTS/GOTS/MOTS options. Vendor/product comparison across 7 axes (1–5 scoring):
- Maturity (TRL alongside ARL)
- Interoperability
- Integration burden
- Cost and availability
- Operational relevance
- Security
- Sustainment and training burden

TAM/TAMM-style market mapping output.

---

### Stage 3 — Concept Development Options

When no suitable COTS exists: up to 3 researched concept development options, each with:
- Purpose and concept description
- Required components
- Likely cost band and development difficulty
- Time to MVP
- Risk, dependencies, potential partners/vendors

**Recommendation types:** Build / Buy / Partner / Adapt / Defer / Terminate

---

### Stage 4 — PoC and Tactical Experimentation Design

Generates full experiment documents including:
- Experiment aim and hypothesis
- Test conditions and scenario
- Training audience, location, enablers
- Safety considerations
- Data collection plan
- Success criteria and decision points

**Pre-built scenario types:** Desert warfare, UxS employment, AI-enabled ISR, autonomous navigation, counter-UxS, mission rehearsal, capability validation.

---

### Stage 5 — Trial Analysis and Reporting

Captures: observations, evidence, metrics, user feedback, operational impact, integration issues, training burden, risks, lessons.

**Result categories:**
- Worked
- Partially worked
- Did not work
- Requires further testing
- Requires redesign
- Requires higher command decision
- Terminate

Root cause analysis uses DLOD/DOTMLPF-P, TEPIDOIL, POPIT.

---

### Stage 6 — Outputs and Recommendations

Generates recommendations for: operational use, TTP development, SOP development, course/training development, CONOPS development, capability development, procurement, further experimentation, integration requirements, or termination/pause.

Produces up to 3 draft CONOPS options. Includes command decision brief format, action tracker, risk register, lessons register, capability development handover template.

---

### Stage 7 — Terminate, Improve, or Scale Decision

Clear metrics and decision gates. Options: Continue / Improve / Scale / Pause / Transfer / Terminate.

**Termination triggers:**
- Poor operational value
- Excessive integration burden
- Safety concerns
- Unsustainable cost
- Inferior COTS alternatives exist
- Lack of user adoption
- Poor reliability
- Failure to meet minimum success criteria

---

## 16 Sections

Dashboard → New Capability Gap → Market Analysis → Product/Vendor Assessment → Concept Options → PoC Builder → Tactical Experimentation Plan → Trial Observation Capture → Metrics and Scoring → CONOPS Generator → TTP/SOP/Course Recommendation → Decision Brief → Action Tracker → Risk Register → Lessons Register → Terminate/Improve/Scale Decision

---

## Architecture

### Shared Case Data Model

One "Case" record flows through all 16 sections. Three pre-populated demo cases:

| ID | Gap | Status |
|----|-----|--------|
| GAP-2026-001 | Counter-UAS (C-UAS) | Fully populated end-to-end |
| GAP-2026-002 | AI-Enabled ISR | Populated through experiment planning |
| GAP-2026-003 | Autonomous UGV | Intake only |

These three cases directly mirror the SBTDWS/TEIW priority capability areas.

### ID Scheme (EXCON Pro conventions)

| Prefix | Record type |
|--------|------------|
| `GAP-YYYY-NNN` | Capability gap records |
| `OPT-NNN` | Concept options |
| `OBS-NNN` | Observations |
| `ACT-NNN` | Actions |
| `RSK-NNN` | Risks |
| `LSN-NNN` | Lessons |
| `INJ-NN-TYPE` | Exercise injects |

### Technical Constraints

- In-memory state only (no localStorage, no CDNs, no network calls) — works fully offline
- Classification banner: 4 levels, colour-coded; default "UNCLASSIFIED // FOR OFFICIAL USE"
- ISO-8601 UTC timestamps
- Navy/slate/olive palette, sharp 4px corners, system-stack typography
- CSS-pure radar chart on metrics screen
- Risk register auto-colours by Likelihood × Impact

### Features

- **Print Brief** — renders active section as A4-paginated briefing
- **Export Summary** — copies plain-text doctrinal summary per section
- Classification banner on every view

---

## Phase 2 Roadmap

1. JSON import/export — cases passed between users and sessions
2. Real inject editor feeding an EXCON Pro-style pipeline
3. Lessons Library cross-case search

---

## Relationship to SBTDWS / TEIW

This platform is the digital governance layer for the [[ADWC Three Wing Structure]]'s TEIW function and the [[ATI-Hub Concept]]'s TEX-Wing. The 7-stage workflow maps directly onto the ATI-Hub's 7-phase innovation pipeline:

| GAP-X Stage | ATI-Hub Phase |
|------------|--------------|
| 1 — Gap Intake | Phase 1 — Problem Definition |
| 2 — Market Analysis | Phase 2 — Sprint Events (research input) |
| 3 — Concept Options | Phase 3 — Prototype Development |
| 4 — PoC Design | Phase 4 — Tactical Evaluation |
| 5 — Trial Analysis | Phase 4 — TEX Report generation |
| 6 — Outputs | Phase 5 — Transition Gate |
| 7 — Scale Decision | Phase 6/7 — Production / HOTO |

---

## Model Selection Used in Build

| Model | Role |
|-------|------|
| Sonnet 4.6 | Doctrinal research dossier (DLOD/DOTMLPF-P/TEPIDOIL/JCIDS/HSEEP/TRL + vignettes for C-UAS, AI-ISR, autonomous UGV) |
| Opus | Information architecture, shared Case data model, scoring rubrics, EXCON Pro alignment, and the build |
| Haiku 4.5 | Structural verification pass |

---

## Source

Ingested from: [[build-capability-gap-platform]] | `.raw/Build military capability gap experimentation platform.md`
