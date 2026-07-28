---
type: reference
title: "CPT Architecture"
created: 2026-06-12
updated: 2026-06-12
tags:
  - capability-planning
  - architecture
  - data-model
  - tool
status: active
related:
  - "[[CPT Overview]]"
  - "[[CPT Reference Frameworks]]"
  - "[[capability-planning-tool/_index]]"
---

# CPT Architecture

Navigation: [[capability-planning-tool/_index]] | [[CPT Overview]] | [[CPT Reference Frameworks]]

Seven-module structure with enforced gating logic. Sequence cannot be bypassed.

---

## Module Structure

| Step | Module | Purpose | Key Output | Gate |
|------|--------|---------|-----------|------|
| 00 | Configure | Define org name, planning horizon, units/teams, capability domains | Organisation baseline | Org name required |
| 01 | Mission Validation | Input and validate mission sets, goals, and objectives | Validated mission list | ≥1 validated mission |
| 02 | Capability Gap Analysis | Identify gaps per mission; classify by domain and DOTMLPF | Capability gap register | ≥1 gap identified |
| 03 | Dependency Mapping | Map which units support which; establish support relationship matrix | Dependency matrix | Optional |
| 04 | Solution Development | Assign solution type to each gap; capture owner and rationale | Solution register | ≥1 solution assigned |
| 05 | Action Plan | Build sequenced, phased actions with owners, timelines, metrics | Phased action plan | None |
| 06 | Summary and Output | Full plan view: heat map, solution breakdown, action table | Complete planning output | None |

---

## Gating Logic

```
[00 Configure] ──(org name required)──►
[01 Missions]  ──(≥1 validated)──────►
[02 Gaps]      ──(≥1 gap)────────────►
[03 Deps]      ──(optional)──────────►
[04 Solutions] ──(≥1 solution)───────►
[05 Actions]   ──(no gate)───────────►
[06 Summary]
```

Gates are soft: users can navigate freely between completed steps, but the tool shows a warning banner when accessing a step whose upstream prerequisites are incomplete.

---

## User Flow

### Step 00 — Configure
- Set organisation name and planning horizon (free text)
- Add units/teams: name + type (Combat, Combat Support, Combat Service Support, Enabling/HQ, Team/Functional)
- Define capability domains — 8 defaults, fully customisable:
  - Command and Control
  - Fires
  - Manoeuvre
  - Logistics
  - Intelligence and ISR
  - Force Protection
  - Communications
  - Training and Readiness

### Step 01 — Mission Validation
- Add missions: title, category (strategic/operational/support/developmental/custom), priority, description
- Set validation status: Validated / Pending Review / Rejected or Deprioritised
- Only validated missions appear in downstream gap analysis
- Key question: what must the organisation actually be able to do? What is a real mission vs aspirational?

### Step 02 — Capability Gap Analysis
- For each validated mission: identify gaps
- Each gap tagged to: capability domain, unit/team (optional), DOTMLPF dimension
- Severity (1–5), current maturity (1–5), target maturity (1–5)
- List view for data entry; Heat Map view for the gap picture
- Key question: what operational effect cannot currently be achieved? Not "we need better kit" — but "we cannot achieve X effect against Y mission."

### Step 03 — Dependency Mapping
- Map which units support which
- Relationship status: Established / Partial / Proposed / Gap
- List view for data entry; Matrix view for the full picture
- Key questions: can any unit already provide what another needs? Where do critical dependencies have no support relationship established?

### Step 04 — Solution Development
- For each gap: assign a solution type (see [[CPT Reference Frameworks]])
- Capture: owner, target timeline, notes/rationale
- Summary dashboard shows distribution across solution types
- Key question: has every organic and shared option been exhausted before escalating?

### Step 05 — Action Plan
- Build sequenced action items linked to solutions
- Each action: title, owner, timeline, resources required, success metric, priority, phase
- Phase is user-defined free text (1/2/3, Near/Mid/Far, FY25/FY26, etc.)
- Actions auto-grouped by phase; sorted by priority within phase
- Key question: what must happen, in what order, owned by whom, resourced how, measured by what?

### Step 06 — Summary and Output
- Key statistics: validated missions, total gaps, critical gaps, action items
- Solution breakdown bar chart
- Gaps by domain bar chart
- Validated mission list
- Sequenced action plan table (phase → priority sorted)

---

## Data Model

### Entity Hierarchy

```
Organisation Config
  └─ Units / Teams (n)
  └─ Capability Domains (n)

Missions (n)
  └─ Capability Gaps (n per mission)
       └─ Solutions (1 per gap)
            └─ Action Items (n per solution)

Dependencies (m × m unit relationship matrix)
```

### Entity Schemas

**Config**
```json
{
  "orgName":  "string",
  "horizon":  "string",
  "units":    [{ "id": "uid", "name": "string", "type": "combat|support|css|enabling|team" }],
  "domains":  ["string"]
}
```

**Mission**
```json
{
  "id":          "uid",
  "title":       "string",
  "category":    "strategic|operational|support|developmental|custom",
  "priority":    "critical|high|medium|low",
  "status":      "validated|pending|rejected",
  "description": "string"
}
```

**Capability Gap**
```json
{
  "id":               "uid",
  "missionId":        "ref:Mission",
  "unitId":           "ref:Unit|null",
  "domain":           "string (from Config.domains)",
  "dimension":        "D|O|T|M|L|P|F|Po",
  "description":      "string",
  "severity":         "1–5",
  "currentMaturity":  "1–5",
  "targetMaturity":   "1–5"
}
```

**Dependency**
```json
{
  "id":               "uid",
  "supportedUnitId":  "ref:Unit",
  "supportingUnitId": "ref:Unit",
  "status":           "established|partial|gap|proposed",
  "description":      "string"
}
```

**Solution**
```json
{
  "id":       "uid",
  "gapId":    "ref:CapabilityGap",
  "type":     "organic|shared|escalated|contracted|accepted",
  "owner":    "string",
  "timeline": "string",
  "notes":    "string"
}
```

**Action Item**
```json
{
  "id":         "uid",
  "solutionId": "ref:Solution|null",
  "title":      "string",
  "owner":      "string",
  "timeline":   "string",
  "resources":  "string",
  "metric":     "string",
  "priority":   "critical|high|medium|low",
  "phase":      "string"
}
```

---

## Configurability

| Element | Configurable | Method |
|---------|-------------|--------|
| Organisation name | Yes | Free text |
| Planning horizon | Yes | Free text |
| Unit names | Yes | Add/remove with type classification |
| Unit types | Yes | 5 options |
| Capability domains | Yes | 8 defaults; add/remove freely |
| Mission categories | Yes | 5 options including Custom |
| Action plan phases | Yes | User-defined free text |
| DOTMLPF dimensions | No | Fixed — standardised framework |
| Solution types | No | Fixed — five-type decision tree |
| Severity scale | No | Fixed — 1–5 |
| Maturity scale | No | Fixed — 1–5 |

DOTMLPF, solution types, and rating scales are fixed because they encode the planning logic itself. Making them configurable would allow users to bypass the structured thinking the tool enforces.
