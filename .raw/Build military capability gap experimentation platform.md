# Build Military Capability Gap Experimentation Platform

**Session ID:** local_df65ecb0-16be-4282-af10-e63a827e1bfa  
**Status:** Idle

---

## Context

This session developed a "Capability Gap to Tactical Experimentation Platform" prototype — a separate workstream loosely based on EXCON Pro, potentially to be integrated later.

---

## User Prompt (Full)

Develop a simple, easy-to-use software product prototype for a "Capability Gap to Tactical Experimentation Platform." Military users need to rapidly assess equipment/technology/capability gaps, compare COTS solutions, generate PoC ideas, design tactical experimentation activities, capture trial results, and turn findings into TTPs, CONOPS, training recommendations, or termination decisions.

**Product ethos:** Reduce paperwork, improve governance, allow staff to spend more time conducting trials, experimentation, and innovation.

### 7-Stage End-to-End Workflow Required

1. **Capability Gap Intake** — Capture operational problem, gap, user need, environment, mission context, urgency, constraints, desired effect. Classify using DLODS/DOTMLPF-P, TEPIDOIL, POPIT, combat functions, readiness impact, risk.

2. **Market and Capability Analysis** — Deep-dive market analysis of relevant equipment, systems, software. Assess COTS/GOTS/MOTS options. Vendor/product comparison: maturity, interoperability, integration burden, cost, availability, operational relevance, security, sustainment, training burden, limitations. TAM/TAMM-style market mapping.

3. **Concept Development Options** — If no suitable COTS exists, generate up to 3 researched concept development options. Each includes: purpose, concept description, required components, likely cost band, development difficulty, time to MVP, risk, dependencies, potential partners/vendors. Recommendation: build, buy, partner, adapt, defer, or terminate.

4. **PoC and Tactical Experimentation Design** — Generate PoC ideas and tactical experimentation documents. Include: experiment aim, hypothesis, test conditions, scenario, training audience, location, enablers, safety considerations, data collection plan, success criteria, decision points. Support: desert warfare, UxS employment, AI-enabled ISR, autonomous navigation, counter-UxS, mission rehearsal, capability validation.

5. **Trial Analysis and Reporting** — Build tools to analyse PoC/trial outcomes. Capture observations, evidence, metrics, user feedback, operational impact, integration issues, training burden, risks, lessons. Categorise results: worked / partially worked / did not work / requires further testing / requires redesign / requires higher command decision / terminate. Root cause analysis using DLODS/DOTMLPF-P, TEPIDOIL, POPIT.

6. **Outputs and Recommendations** — Produce recommendations for: operational use, TTP development, SOP development, course/training development, CONOPS development, capability development, procurement, further experimentation, integration requirements, termination or pause. Generate up to 3 draft CONOPS options. Include command decision brief format, action tracker, risk register, lessons register, capability development handover template.

7. **Termination, Improvement, or Scale Decision** — Clear metrics and decision gates for: continue, improve, scale, pause, transfer, or terminate. Include termination triggers: poor operational value, excessive integration burden, safety concerns, unsustainable cost, inferior COTS alternatives, lack of user adoption, poor reliability, failure to meet minimum success criteria.

### Required Sections (16 total)
Dashboard, New Capability Gap, Market Analysis, Product/Vendor Assessment, Concept Options, PoC Builder, Tactical Experimentation Plan, Trial Observation Capture, Metrics and Scoring, CONOPS Generator, TTP/SOP/Course Recommendation, Decision Brief, Action Tracker, Risk Register, Lessons Register, Terminate/Improve/Scale Decision

---

## Model Selection Used

- **Sonnet** — Doctrinal research dossier (DLOD/DOTMLPF-P/TEPIDOIL/JCIDS/HSEEP/TRL plus vignettes for C-UAS, AI-ISR, autonomous UGV)
- **Opus** — Information architecture, shared "Case" data model, scoring rubrics, EXCON Pro alignment, and the build itself
- **Haiku** — Structural verification pass

---

## Architecture Decisions

### Shared "Case" Data Model
One "Case" record flows through all 16 sections. Three pre-populated demo cases + "New Case" option.

### ID Scheme (EXCON Pro conventions)
- `GAP-YYYY-NNN` — Capability gap records
- `OPT-NNN` — Concept options
- `OBS-NNN` — Observations
- `ACT-NNN` — Actions
- `RSK-NNN` — Risks
- `LSN-NNN` — Lessons
- `INJ-NN-TYPE` — Exercise injects

### Dual-Labelled Taxonomies
- DLOD ↔ DOTMLPF-P (UK/US)
- UK combat functions ↔ US joint warfighting functions
- TRL alongside ARL

### Scoring
- Vendor assessment on 7 axes (1–5)
- PoC viability quick self-rating
- Decision gate visual indicator

### Technical
- In-memory state only (no localStorage, no CDNs, no network calls)
- Classification banner component (4 levels, colour-coded)
- ISO-8601 UTC in domain
- "UNCLASSIFIED // FOR OFFICIAL USE" default
- Navy/slate/olive palette, sharp 4px corners, system-stack typography

---

## Demo Cases Pre-Populated

1. **GAP-2026-001 — Counter-UAS (C-UAS)** — Fully populated end-to-end
2. **GAP-2026-002 — AI-Enabled ISR** — Populated through experiment planning
3. **GAP-2026-003 — Autonomous UGV** — Intake only

---

## Deliverable

**`gap-x-prototype.html`** — Single-file HTML prototype at `Documents\Claude\Projects\EXCON Pro\`

### Features
- 16-section workflow (Dashboard → Intake → Market → Vendor Scorecard → Concepts → PoC → Experiment → Observations → Metrics → CONOPS → TTP/SOP/Course → Decision Brief → Actions → Risks → Lessons → Terminate/Improve/Scale)
- Print Brief renders active section as A4-paginated briefing
- Export Summary copies plain-text doctrinal summary per section
- CSS-pure radar on metrics screen
- Risk register auto-colours by L×I

### Known Scope Simplifications (Phase 1 MVP)
- State doesn't persist across reloads (deliberate)
- CONOPS auto-draft is a skeleton populator, not an LLM call
- Inject scaffold on experiment page is preview-only (six sample injects)

---

## Phase 2 Roadmap
1. JSON import/export so cases can be passed between users
2. Real inject editor feeding an EXCON Pro-style pipeline
3. Lessons Library cross-case search
