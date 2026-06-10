---
type: source
title: "Source: Create Claude Prompt for Concept Brief"
created: 2026-05-27
updated: 2026-05-27
tags:
  - source
  - tactix
  - excon-pro
  - claude-md
status: ingested
related:
  - "[[tactix/_index]]"
  - "[[EXCON Pro Application]]"
---

# Source: Create Claude Prompt for Concept Brief

**Raw file:** `.raw/Create Claude prompt for concept brief.md`  
**Session ID:** local_64de1b67-da04-4145-8b69-b8e773e89d39  
**Ingested:** 2026-05-27  
**Pages created:** (context contributed to [[EXCON Pro Application]])

---

## Summary

The user shared the ExControl Pro concept brief (Dropbox HTML file, v1.7) and asked for a CLAUDE.md file to load project context at the start of each TACTIX session.

### What Was Built

**`Documents\Claude\Projects\EXCON Pro\CLAUDE.md`** (~95 lines)

Strongest load-bearing sections:
- **Domain Model** — 20 document types, 12 tabs, 6 agents, doctrine list, GI vs SI split, named modules (Cyber, HADR, Legal/ROE, Task Force Builder, Lessons Library)
- **Doctrine & Compliance** — "never paraphrase doctrine" guardrail; SI-leakage rule
- **Critical Gotchas** — SI-leakage rule; fixed doc taxonomy (not extensible)
- **Tech Stack** — stubbed with TODOs (fill in once repo exists)
- **Core Commands** — stubbed with TODOs

**`Documents\Claude\Projects\EXCON Pro\CLAUDE_md_chat_transcript.md`** — markdown export of this session, for sharing with collaborators

### Key Guardrails Extracted

1. **SI-leakage rule:** SI content must never appear in GI documents — hard separation
2. **Fixed doc taxonomy:** 20 document types are fixed; no extensions without a version change
3. **Never paraphrase doctrine:** Quote verbatim or cite with precision

### Concept Brief Reference

- **File:** `ExControlPro_ConceptBrief_v1.7.html`
- **URL:** Dropbox (private link)
- **Structure:** 20 doc types, 12 tabs, 6 agents — full domain model
