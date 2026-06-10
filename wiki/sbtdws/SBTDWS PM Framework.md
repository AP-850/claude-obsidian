---
type: reference
title: "SBTDWS PM Framework"
updated: 2026-05-26
tags:
  - sbtdws
  - project-management
  - pm-framework
  - loes
  - laundry-list
status: active
related:
  - "[[SBTDWS 2030 Timeline]]"
  - "[[ADWC Transformation Concept]]"
  - "[[sbtdws/_index]]"
---

# SBTDWS PM Framework

The project management system for the SBTDWS 2030 transformation. Built after identifying that a single-file HTML dashboard was insufficient — rebuilt as a hybrid Excel/HTML architecture.

Navigation: [[sbtdws/_index]] | [[SBTDWS 2030 Timeline]]

---

## System Architecture (Option E: Hybrid)

**Design principle:** HTML is the briefing artifact, not the PM system.

| Component | Role |
|-----------|------|
| `SBTDWS_PM_Master.xlsx` | System of record — live data, multi-user, backed up |
| `SBTDWS_PM_Dashboard.html` | Briefing viewer — loads from Excel, renders for Commander |
| `SBTDWS_PM_System_Guide.docx` | Operations guide — cadence, roles, how to use |
| `refresh_dashboard.py` | Python script — reads Excel, updates dashboard HTML |

**Why hybrid:** Single-user HTML with localStorage loses data. SharePoint/Excel is multi-user, audited, and backed up. Dashboard becomes a read-only view of the master data.

---

## Master Spreadsheet Structure

`SBTDWS_PM_Master.xlsx` — 9 sheets:

| Sheet | Contents |
|-------|----------|
| README | Setup instructions and conventions |
| Project | Project-level metadata |
| Dashboard | Live KPI formulas |
| LOEs | 6 Lines of Effort with descriptions |
| Tasks | 41 tasks across all LOEs, with status/phase/due quarter |
| Gates | Phase gates (MLOC, IOC, FOC) |
| Risks | Risk register |
| People | Role assignments |
| History | Change log |

Status, Phase, and Due Quarter use validated dropdowns.

---

## Dashboard Features

`SBTDWS_PM_Dashboard.html` renders:
- KPI cards
- Progress donuts (pure SVG — no Chart.js or CDN dependency)
- Status breakdown
- LOE progress bar chart
- Full Gantt timeline
- Bilingual EN/AR toggle
- Print to PDF for Commander brief

**Technical note:** Built as fully self-contained (no internet required). CDN dependency issue from earlier version (SheetJS XLSX offline failure) was resolved by switching to pure SVG charts and a Python refresh script.

**Workflow:** Update Excel → run `python refresh_dashboard.py` → open dashboard.html

---

## Six Lines of Effort (LOEs)

| LOE | Description |
|-----|-------------|
| PREP | Foundational Reviews — 6GW training review, CAPDEV portfolio review |
| IW/UW Framework WG | With IWTC/PGI/J7; Camels/Integration KLE; TOs/LOs mapping; Bedouin instructor reroll; phase-out timeline |
| ADD Course Review WG | PGI 5-week comparison; ADNOC pathway; Rollover Trainer decision; terminate/transfer decisions |
| Collective Training Wing | Main Effort; MRE/HICON/EXCON/OT roadmap |
| CAPDEV Portfolio Review | Paramotor, Electric Bikes, UGV, FPV, Documentary, Rollover Trainer, Tactical Resupply Drone |
| Pivot to Tactical Experimentation | Makhlab 1 PoC framework; J3 WDC governance; STC terms; first FDC 5 serial |

---

## 80-Item Laundry List

Full prioritised list in `SBTDWS_Laundry_List_Bilingual.docx` (EN/AR). Priority structure:

| Priority | Count | What it covers |
|----------|-------|---------------|
| P1 — Gates the endstate | 38 | J-Staff, OT cadre, frameworks to write, authorities to confirm, Phase 1 partnership MoUs |
| P2 — Enables IOC by Q4 28 | 32 | OPFOR, HICON, EXCON, live ranges, SCIF, LVC sim suite, industry contracts |
| P3 — Enables FOC or conditional | 10 | Cyber/EW/maritime SQEP, AI/ML compute, coalition framework, ADWC naming |

**Commander observation:** P1 list is dominated by Programmes, Frameworks, and Authorities — not kit. Approximately 21 of 38 P1 items are documents to write, decisions to confirm, or relationships to formalise. This is staff effort and command engagement, not capital expenditure.

---

## Laundry List Categories

| Category | P1 | P2 | P3 | Total |
|----------|----|----|-----|-------|
| People and Cadres | 6 | 5 | 2 | 13 |
| Infrastructure and Facilities | 2 | 11 | 3 | 16 |
| Systems, Kit and Tools | 3 | 5 | 2 | 10 |
| Programmes and Plans | 9 | 2 | 1 | 12 |
| Frameworks, Standards and Documents | 6 | 4 | 0 | 10 |
| Authorities and Writs | 6 | 2 | 1 | 9 |
| External Relationships and Partnerships | 6 | 3 | 1 | 10 |

**Key infrastructure items (P1 only):** Hameem capital plan and J-Staff accommodation. Everything else is P2.

**P3 treatment:** Mostly conditional on external decisions. "Park until decision arrives" — do not let P3 items distract from P1 execution.

---

## Operating Cadence

From `SBTDWS_PM_System_Guide.docx`:

| Cadence | What happens |
|---------|-------------|
| Weekly | LOE Leads update task status; Secretariat reviews for at-risk flags |
| Monthly | Dashboard refreshed; full LOE progress reviewed; risks updated |
| Quarterly | Advisory Board review; kill/continue decisions on active workstreams |
| Annual | Full strategic review; gates assessed; timeline adjusted |

**Roles:**
- Sponsor — command authority; approves gates and kill/continue decisions
- Secretariat — maintains master spreadsheet; runs dashboard refresh; tracks blockers
- LOE Leads — own their LOE, update weekly, escalate risks
- WG Chairs — run working groups within LOEs; produce outputs

---

## Architecture Evolution

**Why the first version was rebuilt:**

1. Built UI before data model → now schema-first
2. One-file architecture → now modular (Excel + HTML + Python)
3. Visuals retrofitted → now designed with data from day one
4. Single-user assumption → now multi-user via Excel/SharePoint
5. No backup strategy → now auto-backup on every Excel save

---

## Source

Ingested from: [[sbtdws-chatgpt-transfer]] | `.raw/Develop SBTDWS transformation response template.md`
