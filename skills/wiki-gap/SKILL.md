---
name: wiki-gap
description: >
  Post-ingest gap analysis for the Obsidian wiki vault. Identifies content gaps, underdeveloped
  pages, missing concepts, unresolved research threads, and cross-domain disconnects. Writes
  a prioritised gap register to wiki/meta/gap-register.md. Triggers on: "/wiki-gap", "gap analysis",
  "what's missing from the wiki", "find gaps", "what should I research next", "post-ingest review".
---

# wiki-gap: Content Gap Analysis

Run manually after a significant ingest session or when you want to identify what to research next. Outputs a prioritised gap register to `wiki/meta/gap-register.md`.

---

## When to Run

- After ingesting a batch of new sources
- When starting a new research thread and wanting to know what's already covered vs missing
- Periodically (every 10–15 new pages) to keep the wiki coherent

---

## Transport

Follow the same transport policy as `wiki-lint`. Read `.vault-meta/transport.json` if present:

- **cli** — `obsidian-cli read "$VAULT" "$NOTE"`
- **mcp-obsidian** / **mcpvault** — `mcp__obsidian-vault__read_multiple_notes`
- **filesystem** — Claude's `Read`/`Glob`/`Grep` (default fallback)

---

## Gap Analysis Process

Work through these checks in order:

### 1. Referenced but Unfiled Concepts
Scan all wiki pages for wikilinks pointing to pages that don't exist. These are implicit research candidates — the vault already knows it needs them.

- Collect all `[[Page Name]]` patterns across `wiki/`
- Check which ones have no corresponding `.md` file
- Group by domain (`sbtdws/`, `tactix/`, `concepts/`, `entities/`, etc.)

### 2. Mentioned but Unlinked Concepts
Scan page bodies for repeated noun phrases or proper nouns that appear in 3+ pages but have no dedicated wiki page and no wikilink. These are invisible gaps — the vault references them but hasn't formalised them.

Focus on:
- Organisation names, acronyms, frameworks, doctrines
- People, roles, units
- Recurring themes or tensions across pages

### 3. Stub and Seed Pages
Identify pages with `status: seed` or `status: stub` in frontmatter, or pages with fewer than 5 substantive lines of content. These exist but need development.

### 4. Underdeveloped Domains
Check each domain `_index.md` against the pages in that folder. Flag domains where:
- The `_index.md` references sub-topics with no page
- Key relationships described in the index aren't cross-linked
- A domain has < 3 pages (may need more depth)

### 5. Cross-Domain Disconnects
The vault has two primary workstreams (SBTDWS/ADWC and TACTIX). Check for:
- Concepts in `wiki/concepts/` that are relevant to both workstreams but only linked from one
- Entities in `wiki/entities/` with no link from either workstream domain
- `wiki/sources/` entries whose findings haven't been reflected in domain pages

### 6. Open Questions Without Answers
Scan `wiki/questions/` for any research questions that haven't been resolved or linked to a finding.

### 7. Hot Cache Threads
Read `wiki/hot.md` — identify any "Active Threads" or flagged items that haven't been addressed in the wiki yet.

---

## Gap Register Format

Create or update `wiki/meta/gap-register.md`:

```markdown
---
type: meta
title: "Gap Register"
updated: YYYY-MM-DD
tags: [meta, gaps]
status: developing
---

# Gap Register

Updated: YYYY-MM-DD | Pages scanned: N | Gaps identified: N

---

## Priority 1 — Missing Pages (Referenced but Unfiled)
Pages wikilinked from existing content but not yet created. High priority — the vault is already pointing at these.

| Gap | Referenced In | Suggested Type | Action |
|-----|--------------|----------------|--------|
| [[Concept Name]] | [[Page A]], [[Page B]] | concept | Create page |

---

## Priority 2 — Invisible Gaps (Mentioned but Unlinked)
Terms appearing in 3+ pages with no dedicated page. Medium priority — worth filing if they'll be referenced again.

| Term | Appears In | Suggested Type |
|------|-----------|----------------|
| "term" | [[Page A]], [[Page B]], [[Page C]] | concept / entity |

---

## Priority 3 — Stub Pages Needing Development
Pages that exist but need substantive content added.

| Page | Domain | Current State |
|------|--------|---------------|
| [[Page Name]] | sbtdws | 3 lines, no sources |

---

## Priority 4 — Cross-Domain Disconnects
Content siloed in one workstream that's relevant to the other.

| Item | Current Domain | Missing Link |
|------|---------------|--------------|
| [[Concept]] | sbtdws | not linked from tactix domain |

---

## Priority 5 — Open Research Threads
Questions or threads from hot cache or questions/ folder without resolution.

| Thread | Source | Status |
|--------|--------|--------|
| "research question" | [[wiki/questions/...]] | unresolved |

---

## Suggested Next Ingests
Based on the gaps above, these are the highest-value research areas:

1. [Topic] — would close N gaps in [domain]
2. [Topic] — would resolve open thread in [[Page]]
3. [Topic] — would develop stub page [[Page]]
```

---

## After Writing the Register

1. Show a brief summary to the user: total gaps by priority tier
2. Ask: "Would you like me to create stub pages for any Priority 1 gaps, or kick off autoresearch on any of the suggested topics?"
3. Do NOT auto-create pages or auto-run research without confirmation

---

## Integration with Other Skills

- **wiki-ingest**: run `wiki-gap` after a large ingest to see what new gaps opened up
- **autoresearch**: feed Priority 1 and Priority 5 items directly as research prompts
- **wiki-lint**: `wiki-gap` focuses on *content* gaps; `wiki-lint` focuses on *structural* health — run both for a full picture
- **wiki-query**: if a gap item is "maybe we already have this somewhere," run a query before flagging it as missing
