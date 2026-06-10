---
type: reference
title: "EXCON Pro Application"
created: 2026-05-27
updated: 2026-06-04
tags:
  - excon-pro
  - exercise-control
  - external-reference
status: active
related:
  - "[[tactix/_index]]"
  - "[[Capability Gap Experimentation Platform]]"
  - "[[TEIW]]"
  - "[[ATI-Hub Concept]]"
---

# EXCON Pro Application (External Reference)

EXCON Pro is an exercise control application led by a colleague. The user has a supporting role only. The colleague holds all source material, concept brief, and CLAUDE.md files. EXCON Pro is **not** a TACTIX product.

EXCON Pro conventions and structure have informed the design of TACTIX (specifically the GAP-X prototype). This page records that reference context only.

See [[tactix/_index]] for the distinction between TACTIX (user-led) and EXCON Pro (colleague-led).

Navigation: [[tactix/_index]] | [[Capability Gap Experimentation Platform]]

---

## Concept Brief Reference

**File:** `ExControlPro_ConceptBrief_v1.7.html`  
**Location:** Dropbox + `Documents\Claude\Projects\EXCON Pro\`  
**CLAUDE.md:** `Documents\Claude\Projects\EXCON Pro\CLAUDE.md` (~95 lines)

---

## Domain Model

### Document Types (20 total)

The application manages 20 distinct document types across the exercise control lifecycle. These are fixed — the taxonomy is not extensible without a version change.

**GI (General Information):** Documents available to all participants.  
**SI (Special Information):** Documents restricted to EXCON/control staff only.

**SI-leakage rule:** SI content must never appear in GI documents. This is a hard guardrail — any merge or copy of SI material into GI output is a failure mode.

### Tabs (12)

The application UI organises content across 12 tabs (exact tab names in the concept brief). Tab structure drives the navigation model for the exercise controller.

### Agents (6)

Six AI agents are defined in the concept brief, each covering a distinct function:

| Agent | Function |
|-------|---------|
| (detail in concept brief) | Drafts / reviews / validates within its domain |

### Named Modules

| Module | Function |
|--------|---------|
| **Cyber** | Cyber effects integration into exercise injects |
| **HADR** | Humanitarian Assistance / Disaster Relief scenario planning |
| **Legal / ROE** | Rules of Engagement compliance checking |
| **Task Force Builder** | Order of battle and force structure management |
| **Lessons Library** | Cross-exercise lessons capture and search |

---

## Doctrine and Compliance

**Critical guardrail:** Never paraphrase doctrine. Doctrine text must be quoted verbatim or cited with precision. Any summary or paraphrase of a doctrinal standard is a compliance failure.

Doctrine list is defined in the CLAUDE.md. The application enforces the GI/SI split at document generation time — no merge path exists between the two classes.

---

## Architecture Decisions

From the GAP-X prototype build session:
- Single-file HTML — no backend, no build step, no runtime dependency
- EXCON Pro ID scheme for case tracking (format: [Module]-[Year]-[SeqNo])
- All state in-browser (sessionStorage / localStorage for Phase 1)
- Phase 2: JSON import/export for persistence and transfer

From the concept brief:
- 7-stage end-to-end workflow (detailed in [[Capability Gap Experimentation Platform]])
- Case data model schema defined (field list in `tactix/master-document.md`)

---

## EXCON Pro Conventions

Key conventions applied consistently across all modules (full table in `tactix/CLAUDE.md`):

- Document IDs follow [Module]-[YYYY]-[NNN] format
- AAR format: observations → analysis → recommendations (not bullet lists)
- Inject format: SITUATION / TASK / EXECUTION (NATO OPORD structure)
- Lessons entries: TITLE / OBSERVATION / LESSON / RECOMMENDATION / STATUS

---

## Current Prototype State

**GAP-X** (`gap-x-prototype.html`) implements the Capability Gap Experimentation workstream:
- 7 stages (Identify Gap → Scope → Design Experiment → Execute → Capture → Validate → Recommend)
- 16 sections across those 7 stages
- 3 demo cases: C-UAS Integration, AI-ISR Platform, Autonomous UGV
- Static data (no import/export yet)

**Remaining modules** are not yet prototyped: Cyber, HADR, Legal/ROE, Task Force Builder, Lessons Library.

---

## Phase 2 Roadmap

| Item | Description |
|------|-------------|
| JSON import/export | Save/load case data as structured JSON |
| Real inject editor | Replace static demo data with editable form |
| Lessons Library | Cross-case search across all completed experiments |
| EXCON Pro ID scheme | Extend from GAP-X to all modules |

---

## Relationship to PG 2030 / SBTDWS

TACTIX and PG 2030 are separate projects. The only legitimate crossover:
- The **TEIW** in ADWC will use GAP-X (or EXCON Pro) as its digital governance layer for experiment tracking
- The ATI-Hub's 7-phase pipeline maps structurally to the 7-stage GAP-X workflow

TACTIX does not own ADWC design decisions. SBTDWS domain files do not own TACTIX architecture decisions.

---

## Sources

- [[excon-pro-claude-prompt]] — CLAUDE.md build session; concept brief analysis
- [[build-capability-gap-platform]] — GAP-X prototype build session
- [[organize-workstreams]] — project separation decision; foundation files created
