---
type: index
title: "TACTIX Domain Index"
created: 2026-05-27
updated: 2026-06-04
tags:
  - tactix
  - domain-index
status: active
related:
  - "[[index]]"
  - "[[EXCON Pro Application]]"
  - "[[Capability Gap Experimentation Platform]]"
  - "[[sbtdws/_index]]"
---

# TACTIX — CAPDEV Innovation Trials and Evaluation Application

TACTIX is the user's own product under development, focused on CAPDEV / Innovation Trials and Evaluation. It is a **separate workstream** from PG 2030 / SBTDWS transformation, though the two share context (TEIW/GAP-X sits at the boundary).

EXCON Pro is a **separate external project** led by a colleague. The user has a supporting role in EXCON Pro only. The colleague holds all source material and CLAUDE.md files for EXCON Pro. EXCON Pro conventions and structure have informed TACTIX design, but they are not the same product.

Future possibility: TACTIX and EXCON Pro may merge as separate products under one company.

Navigation: [[index]] | [[EXCON Pro Application]] | [[Capability Gap Experimentation Platform]]

---

## Domain Pages

| Page | Content |
|------|---------|
| [[EXCON Pro Application]] | External reference: colleague-led exercise control application; EXCON Pro conventions referenced in TACTIX design |
| [[Capability Gap Experimentation Platform]] | GAP-X prototype (TACTIX): 7-stage workflow, 16 sections, 3 demo cases |

---

## Project Boundaries

| Project | Owner | User Role | Source files |
|---------|-------|-----------|-------------|
| TACTIX | User | Lead developer | This vault, `tactix/CLAUDE.md`, `tactix/master-document.md` |
| EXCON Pro | Colleague | Supporting contributor | Held by colleague — not in this vault |

**Rule:** TACTIX work stays in the TACTIX workstream. PG 2030 / SBTDWS stays in the SBTDWS domain. GAP-X (capability gap platform) is TACTIX. The TEIW governance layer in ADWC uses GAP-X; that is the only legitimate crossover point between the two workstreams.

---

## TACTIX Project Folder

`Documents\Claude\Projects\EXCON Pro\` (legacy folder name — holds TACTIX working files)

Key files:
- `gap-x-prototype.html` — single-file HTML prototype (7-stage, 16 sections, 3 demo cases)
- `CLAUDE.md` — project context loaded at start of each TACTIX session
- `CLAUDE_md_chat_transcript.md` — transcript of the CLAUDE.md creation session

---

## TACTIX v2 (Current)

Redesigned prototype built 2026-06-05 based on autoresearch findings. File: `claude-obsidian/tactix-v2.html`

Key changes from GAP-X v1:
- 3 stages (Problem / Experiment / Decision) replacing 7 stages / 16 sections
- 3 role views: Commander (dashboard + decision queue), Analyst (full workflow), Observer (field observation entry)
- Command decision brief as first-class output (generates structured printable brief)
- LocalStorage persistence — cases survive session refresh
- JSON export/import — cases can be shared between users
- 2 pre-built demo cases (C-UAS, TR-UAS) accessible via "Load Demo Data"

## Next Development Priorities

- Lessons Library: cross-case search and pattern extraction
- Lessons register linked to a shared knowledge base
- Multi-case lessons summary for After Action Review
- EXCON Pro alignment (if/when collaboration begins)

---

## Sources

- [[organize-workstreams]] — session separating PG 2030 and TACTIX into distinct workstreams
- [[excon-pro-claude-prompt]] — session building CLAUDE.md from ExControlPro_ConceptBrief_v1.7.html
- [[build-capability-gap-platform]] — GAP-X prototype build session
