# Organize Two Projects Into Separate Workstreams

**Session ID:** local_a28f8d38-ea8a-4c61-b58c-d42d7b5ca291  
**Status:** Idle

---

## User

There are currently two main projects I am working on: PG 2030, and the development of the TACTIX Application (using EXCON Pro as a handrail). There has been significant work done on both, but mainly on PG 2030. I feel like the information is sometimes being repeated and crossing over between projects. I want to consolidate my thoughts and separate the two into distinct and separate workstreams. I want to develop core project documents that can be referenced as foundations to save on having to go over everything from scratch each time we work on it. What is the best way to do this? I believe we need to develop a claude md file for each one and a detailed master document that has captured the work and analysis so far.

## Assistant

This is a really smart move — having two active, complex projects bleeding into each other in conversation creates real drag. The approach you're describing (CLAUDE.md + master document per project) is exactly right, and we have a skill built for this.

*(Loaded memory-management skill, reviewed sessions, synthesized context from all previous sessions)*

## Assistant — Summary of Work Done

After reviewing all previous sessions (8 total), the assistant built four project foundation files:

### PG 2030 (`pg-2030/` folder):

**`CLAUDE.md`** — Hot cache covering:
- All key acronyms (30+)
- Key people and organisations
- Active workstreams
- Guiding philosophy
- Milestone timeline
- File locations

**`master-document.md`** — Full project record covering:
- Background and strategic context
- The 19 DMTs and 4 MRCs
- The 9 directed tasks with READY/PARTIAL/DEVELOPING/GAP status
- Three-wing ADWC model (DWW/CTVMR/TEIW) with Australian CTC-L/JTW mapping
- All key relationships and dependencies
- PM framework structure
- WG submission format
- Analytical frameworks
- Three development thematics
- Decisions/issues log
- All deliverables produced
- Standing risk register

### TACTIX (`tactix/` folder):

**`CLAUDE.md`** — Hot cache covering:
- The 16 application sections
- EXCON Pro conventions table
- Current prototype state
- Phase 2 roadmap
- Design principles
- Hard separation from PG 2030

**`master-document.md`** — Full product record covering:
- Origin and EXCON Pro relationship
- Complete 7-stage end-to-end workflow
- Architecture decisions
- Case data model schema
- All EXCON Pro conventions implemented
- Three demo cases
- Known scope simplifications
- Phase 2 roadmap
- Research frameworks incorporated

## Recommendation

Copy the `pg-2030/` and `tactix/` folders into your OneDrive alongside existing project folders (`Documents\PG FDR 2030\` and `Documents\Claude\Projects\EXCON Pro\`). At the start of any future session on either project, attach or reference the relevant `CLAUDE.md` to avoid rebuilding context from scratch.
