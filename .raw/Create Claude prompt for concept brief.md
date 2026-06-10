# Create Claude Prompt for Concept Brief

**Session ID:** local_64de1b67-da04-4145-8b69-b8e773e89d39  
**Status:** Idle

---

## User

Can you please suggest a succinct and specific Claude md file prompt for this:

https://www.dropbox.com/scl/fi/ct4wywxno3qtnmvlwki3k/ExControlPro_ConceptBrief_v1.7.html?rlkey=69u4lvsxn06xicz1d34b78mpl&st=pde8alw8&dl=0

## Assistant

*(Fetched the Dropbox URL via Claude in Chrome, read the ExControl Pro concept brief HTML, extracted domain context)*

Built and saved a CLAUDE.md file to `Documents\Claude\Projects\EXCON Pro\CLAUDE.md`.

### Key Sections in the CLAUDE.md

- **Domain Model** — 20 document types, 12 tabs, 6 agents, doctrine list, GI vs SI split, named modules (Cyber, HADR, Legal/ROE, Task Force Builder, Lessons Library)
- **Doctrine & Compliance** — Critical for accuracy; contains the "never paraphrase doctrine" guardrail
- **Critical Gotchas** — SI-leakage rule, fixed doc taxonomy
- **Tech Stack** — Stubbed with TODOs (fill in once repo exists)
- **Core Commands** — Stubbed with TODOs

File is ~95 lines, well under the 200–300 line ceiling. Strongest load-bearing sections are Domain Model, Doctrine & Compliance, and Critical Gotchas.

---

## User

How do I share this with another Claude user?

## Assistant

A CLAUDE.md is just a plain markdown file. Main sharing paths:

1. **Send the file** — Email/Slack/OneDrive. They save it as `CLAUDE.md` at root of matching project folder.
2. **Commit to the repo** — CLAUDE.md is treated like any other source file; anyone who clones gets the same project memory.
3. **Wrap in a plugin** — Use `create-cowork-plugin` skill to bundle skills, agents, MCP configs into a shareable plugin.

---

## User

No, I meant how do I share this entire chat with another Claude user?

## Assistant

Cowork sessions live locally on your machine — no built-in share link. The workaround is to export the transcript as a file. Options: Markdown or HTML.

---

## User

Markdown

## Assistant

*(Wrote the chat transcript from context since the session tool can't read its own running transcript)*

**Deliverable:** `Documents\Claude\Projects\EXCON Pro\CLAUDE_md_chat_transcript.md`

Send this file alongside `CLAUDE.md` — the transcript gives the other person the reasoning, the CLAUDE.md is the actual artefact.
