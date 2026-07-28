---
tags:
  - capability-planning
  - transformation
  - tool-development
  - frameworks
  - strategy
created: 2025-06-12
status: in-progress
project: Capability Planning Tool
---

# Capability Planning Tool — Project Master Note

> **Core idea:** An organisation-agnostic, capability-led planning tool that enforces the correct planning sequence — mission first, capability second, structure third, support fourth, action plan last.

---

## Table of Contents

- [[#1. Project Purpose]]
- [[#2. The Planning Problem]]
- [[#3. The Core Planning Logic]]
- [[#4. Research — Existing Frameworks]]
  - [[#4.1 Military & Defence Frameworks]]
  - [[#4.2 Enterprise Architecture Frameworks]]
  - [[#4.3 Commercial Transformation Frameworks]]
  - [[#4.4 Framework Synthesis Table]]
  - [[#4.5 Critical Gaps in Existing Tools]]
- [[#5. Tool Architecture]]
  - [[#5.1 Design Philosophy]]
  - [[#5.2 Module Structure]]
  - [[#5.3 Sequence & Gating Logic]]
  - [[#5.4 Data Model]]
  - [[#5.5 User Flow (Step by Step)]]
- [[#6. Reference Frameworks Built Into the Tool]]
  - [[#6.1 DOTMLPF Dimensions]]
  - [[#6.2 Solution Type Decision Logic]]
  - [[#6.3 Maturity Scale]]
  - [[#6.4 Severity Scale]]
- [[#7. Configurability]]
- [[#8. Outputs]]
- [[#9. Design Decisions & Rationale]]
- [[#10. Future Extensions]]
- [[#11. Build Log]]

---

## 1. Project Purpose

This tool is designed for any organisation — military, government, corporate, or otherwise — that needs to plan a genuine capability transformation rather than produce a list of activities dressed up as a strategy.

The tool enforces a planning logic derived from military capability-based planning doctrine, enterprise architecture frameworks, and commercial transformation methodologies — distilled into a seven-step sequence that cannot be shortcut.

**What the tool is NOT:**
- A project management tool
- A task tracker
- A calendar or sync matrix builder
- A way to quickly generate an action plan

**What the tool IS:**
- A structured thinking environment that forces the right questions in the right order
- A capability gap register linked to missions and solutions
- A dependency mapper that reveals whether gaps can be closed internally or require escalation
- An action plan generator that earns its outputs through upstream logic

---

## 2. The Planning Problem

Most transformation planning starts in the wrong place. Organisations move straight to a calendar, a list of training events, or an equipment wish-list — and call it a plan.

The problem is that **tactical activity planning is not transformation**. Improving a course, running a shooting competition, or buying new kit are business-as-usual activities. They do not constitute a capability transformation unless they are derived from a deliberate analysis of:

1. What the organisation must be able to do (missions)
2. What it cannot currently do (capability gaps)
3. Why it cannot do it (DOTMLPF root cause)
4. Who can help (dependencies and support relationships)
5. How to close the gap (solution type: organic, shared, escalated, contracted, or accepted as risk)
6. What structural trade-offs are required (force design decisions)
7. What must happen, in what order, owned by whom (action plan)

**The action plan is the last step, not the first.**

---

## 3. The Core Planning Logic

```
MISSION FIRST → CAPABILITY SECOND → STRUCTURE THIRD → SUPPORT FOURTH → ACTION PLAN LAST
```

Rendered as a flow:

```
Validate Missions / Goals
        ↓
Identify Capability Gaps (per mission, per unit, by DOTMLPF dimension)
        ↓
Map Dependencies (who supports whom; what is already established vs gap)
        ↓
Develop Solution Options (organic / shared / escalated / contracted / accepted)
        ↓
Confirm Force Design Direction (trade-offs, consolidations, priorities)
        ↓
Functional Support Planning (what enabling organisations must do)
        ↓
Build the Action Plan, Sync Matrix, Long-Range Calendar
```

> **Key principle:** Do not build the calendar first. Build the logic first.

---

## 4. Research — Existing Frameworks

### 4.1 Military & Defence Frameworks

#### Capabilities-Based Planning (CBP)

**Origin:** US Department of Defense, 2001 Quadrennial Defense Review. Shift from threat-based to capability-based planning.

**Core logic:** A top-down decision-making process focused on *what* to achieve rather than *how to complete projects*. Starts from the mission/policy level and cascades down to capability requirements.

**Process:**
1. Analyse policy guidance and security environment
2. Model future environment and scenarios
3. Identify required capabilities from scenarios
4. Identify gaps against current and programmed capabilities
5. Develop solutions

**What it contributes to this tool:**
- Mission-first cascade logic
- Top-down design philosophy
- Scenario-based gap identification

**Limitations:**
- Heavily reliant on classified threat models
- Architecture frameworks and CBP processes are not linked in an obvious way — difficult for non-specialists
- Not easily transferred to a generic, organisation-agnostic tool

---

#### DOTMLPF / DOTMLPF-P

**Origin:** US Joint Chiefs of Staff — embedded in JCIDS (Joint Capabilities Integration and Development System)

**What it is:** An eight-dimensional framework for classifying capability gaps and their solutions. Prevents organisations from defaulting to equipment procurement when the gap might actually be in doctrine, training, or leadership.

| Code | Dimension | Covers |
|------|-----------|--------|
| D | Doctrine | How the organisation operates; principles and guidance |
| O | Organisation | Structure, command relationships, force design |
| T | Training | Individual and collective training standards |
| M | Materiel | Equipment, platforms, systems, supplies |
| L | Leadership & Education | Leader development, professional education |
| P | Personnel | Availability of qualified people; manpower |
| F | Facilities | Infrastructure, ranges, installations |
| Po | Policy | Governing rules, authorities, legal constraints |

**Key insight:** A deficiency in any one dimension adversely impacts the whole capability. Solutions must be integrated across the spectrum, not siloed to materiel.

**What it contributes to this tool:**
- Eight-dimensional gap classification (built into the gap analysis module)
- Forces planners to consider non-material solutions before jumping to procurement
- Distinguishes between material solutions (new systems) and non-material solutions (doctrine, training, org change)

**Limitations:**
- Bureaucratic and document-heavy in native form
- Policy dimension is US-specific in its original framing

---

#### JCIDS — Capabilities-Based Assessment (CBA)

**Origin:** US Joint Capabilities Integration and Development System

**Three-phase CBA process:**

| Phase | Name | What it does |
|-------|------|-------------|
| 1 | Functional Area Analysis (FAA) | Identifies operational tasks, conditions, and standards needed to accomplish objectives |
| 2 | Functional Needs Analysis (FNA) | Assesses whether current and programmed capabilities can accomplish those tasks; outputs list of gaps |
| 3 | Functional Solutions Analysis (FSA) | Evaluates DOTMLPF solutions for each gap; distinguishes material vs non-material approaches |

**Key insight:** The FSA explicitly asks: *Can this gap be solved without buying new equipment?* Only after exhausting non-material options is a material solution (new acquisition) recommended.

**What it contributes to this tool:**
- FAA → FNA → FSA as the core three-phase gap analysis workflow
- Clear separation of *identifying* gaps from *proposing* solutions
- Escalation logic: non-material first, material second, external acquisition last

**Limitation noted in research:** JCIDS addresses reported gaps rather than anticipating future gaps. The process is also consensus-heavy and slow by design.

---

#### NATO Defence Planning Process (NDPP)

**What it is:** A five-step, four-year planning cycle for identifying and delivering alliance capabilities.

**Five steps:**
1. Establish Political Guidance
2. Determine Requirements → Gap Analysis (Shortfalls / Surplus / To be maintained) → Shortfall Prioritisation
3. Apportion Requirements and Set Targets
4. Facilitate Implementation *(continuous)*
5. Review Results

**Key insight:** The NATO gap analysis step produces three categories — shortfalls, surplus, and maintained — not just a list of problems. And shortfall prioritisation is a structured output, not an afterthought.

**What it contributes to this tool:**
- Shortfall / surplus / maintained classification (adapted into severity + solution type)
- Multi-tier allocation logic: what sits at unit level, what sits at HQ level, what requires alliance/external action → directly maps to organic / shared / escalated
- 20-year planning horizon demonstrates the importance of long-range thinking vs. tactical activity

---

### 4.2 Enterprise Architecture Frameworks

#### TOGAF — The Open Group Architecture Framework

**What it is:** An eight-phase Architecture Development Method (ADM) used in enterprise IT and business transformation.

**Relevant phases:**
- **Phase A** — Architecture Vision: define scope and capability objectives
- **Phase B** — Business Architecture: build capability map, conduct gap analysis, apply heat mapping
- **Phase E** — Opportunities & Solutions: develop capability roadmap
- **Phase F** — Migration Planning: sequence the transition from current to target state

**Capability heat mapping:** In Phase B, capabilities are plotted on a heat map showing maturity (current vs. target), effectiveness, performance, and value. This is the primary visual output for gap analysis.

**Four maturity dimensions (TOGAF):**
1. People
2. Process
3. Technology
4. Information

**What it contributes to this tool:**
- Capability heat map as a visual output layer (domain × severity)
- Current vs. target maturity as the core gap measurement
- Dependency mapping between capabilities and organisational units
- "Build, buy, improve, or retire" taxonomy → adapted to organic/shared/escalated/contracted/accepted

**Key insight from research:** Because capabilities change slowly while processes and technologies change frequently, they provide a durable planning framework. Plan around WHAT the organisation needs to do, then determine HOW to enable those capabilities.

---

#### Business Capability Mapping (BCM)

**What it is:** A structured approach to documenting and visualising organisational capabilities, widely used in enterprise architecture and digital transformation.

**Hierarchy:** Level 1 → Level 2 → Level 3 capability decomposition

**Capability-to-capability dependency map:** Each capability is assessed for whether it drives or is driven by every other capability — creating a matrix of interdependencies. This reveals which capabilities are foundational (must be built first) and which are dependent (cannot be achieved without others).

**What it contributes to this tool:**
- Hierarchical capability decomposition scales from strategic to tactical
- Dependency matrix structure (adapted as the unit-to-unit dependency module)
- Heat map + capability roadmap as the standard output pair

---

### 4.3 Commercial Transformation Frameworks

#### McKinsey 7S Framework

**Seven interdependent elements:**
1. Strategy
2. Structure
3. Systems
4. Shared Values
5. Skills
6. Style
7. Staff

**Relevance:** The 7S model highlights that capability gaps are never just about equipment or training — they reflect misalignments across structure, leadership culture, systems, and people simultaneously. An organisation can have the right equipment and doctrine but still fail to close a capability gap because leadership culture or staff availability is misaligned.

**What it contributes to this tool:** The DOTMLPF dimension tagging in the gap analysis module serves a similar function — forcing users to identify *which* dimension the gap sits in, not just what the gap is.

---

#### Capability Heat Mapping (Commercial Practice)

Used widely in supply chain, digital transformation, and enterprise architecture as a prioritisation and sequencing tool.

**The CBP Cycle:** Map → Assess → Plan → Control

**What a heat map does:**
- Displays capabilities in a colour-coded matrix
- Rates current performance and maturity
- Defines target states by time horizon
- Highlights gaps, owners, and dependencies
- Turns a diffuse list of "things to fix" into a structured view linked to outcomes

**What it contributes to this tool:** The heat map is the primary visual output of the gap analysis module — domain vs. average severity, colour-coded from green (no gaps) through yellow/orange to red (critical).

---

### 4.4 Framework Synthesis Table

| Framework | Origin | Best Contribution to This Tool |
|-----------|--------|-------------------------------|
| CBP (Military) | US DoD | Mission-first logic; top-down cascade from goal → capability → gap |
| DOTMLPF | US Joint Chiefs | Eight-dimensional gap classification; prevents equipment-only thinking |
| JCIDS / CBA | US JCIDS | FAA → FNA → FSA workflow; separates gap identification from solution development |
| NATO NDPP | NATO | Shortfall/surplus/maintained; tiered allocation (internal/shared/external) |
| TOGAF / BCM | Open Group | Capability heat mapping; current vs target maturity; dependency mapping |
| McKinsey 7S | McKinsey | Gaps live across structure, people, culture — not just materiel |
| CBP Cycle | Commercial | Map → Assess → Plan → Control as the iterative planning rhythm |

---

### 4.5 Critical Gaps in Existing Tools

Five weaknesses appear consistently across all existing frameworks — these are where this tool must go further:

**Gap 1 — Dependency and supporting/supported relationships are poorly handled**
Architecture frameworks and CBP processes are not linked in an obvious way. Military experts and decision-makers involved in capability planning are only rarely able to deepen their understanding without personnel specialised in these tools. This tool makes cross-unit dependency mapping intuitive, not expert-dependent.

**Gap 2 — Most tools default to acquisition, not transformation**
JCIDS, DOTMLPF, and TOGAF all tend to funnel users toward procurement or technology solutions. This tool has an explicit non-material solution pathway that asks users to exhaust internal and cross-organisational options before escalating.

**Gap 3 — Force design trade-off decisions are not supported**
Existing tools identify gaps and propose solutions, but none systematically help leaders make the hard choices about what to deprioritise, consolidate, or accept as risk. This tool includes a dedicated solution type — "Accepted Risk" — that requires documented rationale.

**Gap 4 — The action plan is treated as the starting point, not the output**
Most tools jump to action before the capability logic is established. This tool's architecture enforces the correct sequence through module gating.

**Gap 5 — Escalation pathways are implicit, not structured**
No existing tool provides a clean, configurable decision tree for when a gap should be: solved organically, shared, escalated, outsourced, or accepted as risk. This tool's Solution module makes this explicit and required.

---

## 5. Tool Architecture

### 5.1 Design Philosophy

> The tool enforces a strict planning sequence that prevents users from jumping to an action plan before completing the upstream reasoning. Each module gates the next. This is not a constraint — it is the product's core value proposition.

Three non-negotiables:
1. **Sequence is enforced** — the logic chain cannot be bypassed
2. **The action plan is earned** — it is produced by the tool after upstream thinking is complete, not entered as a starting assumption
3. **Organisation-agnostic** — no military terminology is hardcoded; all labels are configurable

---

### 5.2 Module Structure

| Step | Module | Purpose | Key Output | Gate |
|------|--------|---------|-----------|------|
| 00 | **Configure** | Define org name, planning horizon, units/teams, capability domains | Organisation baseline | Org name required |
| 01 | **Mission Validation** | Input and validate mission sets, goals, and assigned objectives | Validated mission list | ≥1 validated mission |
| 02 | **Capability Gap Analysis** | Identify capability gaps per mission; classify by domain and DOTMLPF | Capability gap register | ≥1 gap identified |
| 03 | **Dependency Mapping** | Map which units support which; establish support relationship matrix | Dependency matrix | Optional |
| 04 | **Solution Development** | Assign solution type to each gap; capture owner and rationale | Solution register | ≥1 solution assigned |
| 05 | **Action Plan** | Build sequenced, phased actions with owners, timelines, and metrics | Phased action plan | None |
| 06 | **Summary & Output** | Full plan view: heat map, solution breakdown, action table | Complete planning output | None |

---

### 5.3 Sequence & Gating Logic

```
[00 Configure] ──(org name required)──►
[01 Missions]  ──(≥1 validated)──────►
[02 Gaps]      ──(≥1 gap)────────────►
[03 Deps]      ──(optional)──────────►
[04 Solutions] ──(≥1 solution)───────►
[05 Actions]   ──(no gate)───────────►
[06 Summary]
```

Gates are soft in the sense that users can navigate freely between completed steps, but the tool will show a warning banner when they try to work in a step whose upstream prerequisites are incomplete.

---

### 5.4 Data Model

#### Entity Hierarchy

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

#### Entity Schemas

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

### 5.5 User Flow (Step by Step)

#### Step 00 — Configure
- Set organisation name and planning horizon (free text; e.g. "2030", "FY27", "3-Year Plan")
- Add units/teams: name + type (Combat/Manoeuvre, Combat Support, Combat Service Support, Enabling/HQ, Team/Functional)
- Define capability domains — 8 defaults provided, fully customisable:
  - Command & Control
  - Fires
  - Manoeuvre
  - Logistics
  - Intelligence & ISR
  - Force Protection
  - Communications
  - Training & Readiness

#### Step 01 — Mission Validation
- Add missions with: title, category, priority, description
- Set validation status: **Validated** / **Pending Review** / **Rejected / Deprioritised**
- Status can be toggled at any time
- Only validated missions appear in downstream gap analysis
- *Key question at this step:* What must the organisation actually be able to do? What is a real mission, and what is aspirational or out of scope?

#### Step 02 — Capability Gap Analysis
- For each validated mission: identify gaps
- Each gap is tagged to:
  - A capability domain (from config)
  - A unit/team (optional)
  - A DOTMLPF dimension (which root cause category?)
- Severity rating (1–5)
- Current maturity rating (1–5)
- Target maturity rating (1–5)
- **List view** for data entry; **Heat Map view** for the gap picture
- *Key question at this step:* What operational effect cannot currently be achieved? Not "we need better kit" — but "we cannot achieve X effect against Y mission."

#### Step 03 — Dependency Mapping
- Map which units support which
- For each relationship: Established / Partial / Proposed / Gap (not currently provided)
- **List view** for data entry; **Matrix view** for the full picture
- *Key questions at this step:* Can any unit already provide what another needs? Where do support relationships exist but are undocumented? Where do critical dependencies have no support relationship established?

#### Step 04 — Solution Development
- For each gap: assign a solution type (see [[#6.2 Solution Type Decision Logic]])
- Capture: owner, target timeline, notes/rationale
- Summary dashboard shows distribution across solution types
- *Key question at this step:* Has every option to solve this organically or through internal sharing been exhausted before escalating? What is the billpayer for each solution?

#### Step 05 — Action Plan
- Build sequenced action items linked to solutions
- Each action: title, owner, timeline, resources required, success metric, priority, phase
- Phase is user-defined (1/2/3, Near/Mid/Far, FY25/FY26/FY27, etc.)
- Actions auto-grouped by phase; sorted by priority within phase
- *Key question at this step:* What must happen, in what order, owned by whom, resourced how, measured by what?

#### Step 06 — Summary & Output
- Key statistics: validated missions, total gaps, critical gaps, action items
- Solution breakdown bar chart
- Gaps by domain bar chart
- Validated mission list
- Sequenced action plan table (phase → priority sorted)

---

## 6. Reference Frameworks Built Into the Tool

### 6.1 DOTMLPF Dimensions

Used to classify the root cause of every capability gap.

| Code | Full Name | What It Covers | Example Gap |
|------|-----------|----------------|-------------|
| D | Doctrine | Principles, guidance, how the org operates | No doctrine exists for multi-domain entry operations |
| O | Organisation | Structure, command relationships, force design | No dedicated ISR unit; capability is fragmented |
| T | Training | Individual and collective training standards | Units cannot integrate fires with manoeuvre at brigade level |
| M | Materiel | Equipment, platforms, systems, supplies | No organic counter-UAS system below battalion |
| L | Leadership & Education | Leader development, professional education | Commanders lack understanding of EW capabilities |
| P | Personnel | Availability of qualified people; manpower | Insufficient qualified signals operators |
| F | Facilities | Infrastructure, ranges, installations | No simulation facility for CBRN training |
| Po | Policy | Governing rules, authorities, legal constraints | Policy prevents use of certain ISR systems domestically |

> **Rule of thumb:** If the gap would persist even after buying new equipment, it is not a Materiel gap.

---

### 6.2 Solution Type Decision Logic

```
Can the gap be closed by the unit itself?
    YES ──► ORGANIC
            (Developed and held within the unit)
    
    NO ──► Can another internal team/unit provide it?
               YES ──► SHARED
                        (Cross-team or cross-unit support arrangement)
               
               NO ──► Does closing it require a higher authority
                       decision, resource, or external body?
                           YES ──► ESCALATED
                                    (Requires higher authority or external organisation)
                           
                           NO ──► Can a contractor or external partner deliver it?
                                       YES ──► CONTRACTED
                                                (External partner or contractor)
                                       
                                       NO ──► ACCEPTED RISK
                                               (Gap acknowledged; not currently resourced)
                                               (Document rationale)
```

**Decision logic principle:** Work inward-out. Always exhaust internal organic options first, then internal shared options, before escalating or contracting. Accepting risk is a last resort that requires explicit documentation — it is not a default.

---

### 6.3 Maturity Scale (Current & Target)

| Level | Label | Description |
|-------|-------|-------------|
| 1 | None | Capability does not exist |
| 2 | Initial | Ad hoc; relies on individuals; not repeatable |
| 3 | Developing | Some process exists; partially repeatable |
| 4 | Capable | Defined, documented, and consistently delivered |
| 5 | Advanced | Optimised; continuously improved; exportable |

> The gap between Current Maturity and Target Maturity defines the transformation requirement. A gap from 2→4 is different in scale and nature from a gap from 1→5.

---

### 6.4 Severity Scale

| Level | Label | Planning Implication |
|-------|-------|---------------------|
| 1 | Minor | Can be tolerated; low priority |
| 2 | Low | Should be addressed but not urgent |
| 3 | Moderate | Affects mission delivery; medium priority |
| 4 | High | Significantly degrades mission capability |
| 5 | Critical | Mission cannot be achieved without resolution |

> Critical and High severity gaps should drive prioritisation in the Action Plan. Accepted Risk solutions for Critical gaps must be explicitly flagged to leadership.

---

## 7. Configurability

| Element | Configurable | Method |
|---------|-------------|--------|
| Organisation name | ✅ | Free text |
| Planning horizon | ✅ | Free text |
| Unit names | ✅ | Add/remove with type classification |
| Unit types | ✅ | 5 options (Combat, CS, CSS, Enabling, Team) |
| Capability domains | ✅ | 8 defaults; add/remove freely |
| Mission categories | ✅ | 5 options including Custom |
| Action plan phases | ✅ | User-defined free text |
| DOTMLPF dimensions | ❌ | Fixed — standardised framework |
| Solution types | ❌ | Fixed — five-type decision tree |
| Severity scale | ❌ | Fixed — 1–5 |
| Maturity scale | ❌ | Fixed — 1–5 |

**Design rationale for fixed elements:** DOTMLPF, solution types, and the rating scales are fixed because they encode the planning logic itself. Making them configurable would allow users to bypass the structured thinking the tool is designed to enforce.

---

## 8. Outputs

### 8.1 Primary Outputs

| Output | Description |
|--------|-------------|
| Capability Gap Register | All gaps with mission, unit, domain, DOTMLPF dimension, severity, current/target maturity |
| Dependency Matrix | m×n grid of unit-to-unit support relationships with status |
| Solution Register | All gaps with assigned solution type, owner, timeline, and rationale |
| Sequenced Action Plan | Phased table: owner, timeline, resources, metric, solution type |

### 8.2 Visual Outputs

| Output | Description |
|--------|-------------|
| Capability Heat Map | Domain × average severity; colour-coded from none to critical |
| Solution Breakdown | Bar chart of solution type distribution |
| Maturity Gap View | Current vs target maturity per gap (colour-coded dots) |
| Dependency Matrix | Visual grid showing established/partial/gap/proposed relationships |

### 8.3 Planning Metrics (Summary Dashboard)

- Validated missions count
- Total capability gaps
- Critical gaps (severity ≥ 4)
- Total action items
- Gaps resolved organically vs. escalated vs. accepted as risk
- Actions by phase and priority

---

## 9. Design Decisions & Rationale

### Why DOTMLPF and not a simpler classification?
DOTMLPF is the most rigorous and widely validated framework for classifying capability gaps. Its eight dimensions are specifically designed to stop planners from treating every problem as an equipment problem. It is used by the US, UK, NATO, and allied forces precisely because it works at scale across diverse contexts. For a commercial context, the same dimensions apply — substitute "doctrine" for "operating procedures" and "materiel" for "systems/technology."

### Why five solution types and not three?
The five types (Organic / Shared / Escalated / Contracted / Accepted Risk) map directly onto the decision logic that planners actually face. Three types would conflate "we can get a partner to do this" with "we need HQ approval and funding" — which are fundamentally different escalation paths with different timelines, authorities, and risks.

### Why is the action plan gated?
The most common failure mode in transformation planning is producing an activity list and calling it a plan. Gating the action plan behind mission validation, gap identification, and solution development forces planners to earn the action plan through upstream thinking. The tool cannot produce a meaningful plan without that work; the gate enforces the logic.

### Why are phases user-defined?
Different organisations use different temporal frameworks (fiscal years, programme phases, calendar years, near/mid/far term). Forcing a specific phase structure would reduce configurability without adding planning value.

### Why is dependency mapping optional?
Not all organisations have meaningful inter-unit dependencies to map, particularly smaller or single-unit deployments. Making it optional preserves the tool's universal applicability. Users who skip it are not penalised — but they miss the visibility that cross-unit dependency mapping provides.

---

## 10. Future Extensions

| Module | Priority | Description |
|--------|----------|-------------|
| **Force Design Review** | High | Structured trade-off decision capture — what to consolidate, deprioritise, or repurpose; explicit billpayer decisions |
| **Sync Matrix** | High | Visual calendar/timeline view of actions against milestones and phases |
| **Risk Register** | Medium | Formal risk log linked to accepted-risk gaps; likelihood × impact scoring |
| **Progress Tracking** | Medium | RAG status updates against action items over time; completion tracking |
| **Export** | Medium | PDF/DOCX generation of the full planning output for briefings |
| **Multi-Org / Coalition** | Low | Support for cross-organisation planning where gaps span multiple entities |
| **Scenario Library** | Low | Pre-loaded mission scenario templates for common planning contexts |
| **Weighted Prioritisation** | Low | Analytical Hierarchy Process (AHP) scoring to rank gap priorities across competing criteria |

---

## 11. Build Log

### Session 1 — 2025-06-12

**Research completed:**
- Reviewed Capabilities-Based Planning (CBP) — DoD, RAND, Army War College
- Reviewed DOTMLPF/DOTMLPF-P — JCIDS, AcqNotes, Marine Corps CBA doctrine
- Reviewed NATO NDPP five-step process
- Reviewed TOGAF Business Capability Planning (ADM Phases A/B/E/F)
- Reviewed Business Capability Mapping and heat mapping practice
- Reviewed McKinsey 7S and BCG DAI as commercial comparators
- Identified five critical gaps in all existing frameworks

**Architecture completed:**
- Seven-module structure defined
- Data model specified (six entity types)
- User flow documented (step by step)
- Gating logic defined
- DOTMLPF integration designed
- Solution type decision tree mapped
- Maturity and severity scales defined
- Configurability matrix documented

**Tool built:**
- Full React application (`capability-planning-tool.jsx`)
- Seven working modules with real data entry
- Storage API persistence (auto-save)
- Capability gap heat map
- Dependency matrix view
- Solution type distribution
- Phased action plan with summary table
- Dark sidebar / amber accent design with vertical progress thread

**Files created:**
- `capability-planning-tool.jsx` — interactive React application
- `capability-planning-tool-architecture.md` — architecture design document
- `Capability-Planning-Tool-Project.md` — this master note

---

### Open Questions / Next Steps

- [ ] Build Force Design Review module (trade-off decision capture)
- [ ] Build Sync Matrix / visual timeline view
- [ ] Add export function (PDF or DOCX)
- [ ] Consider adding a weighted prioritisation method (AHP) for gap ranking
- [ ] Review DOTMLPF dimension labels for non-military context — consider alternate labelling option
- [ ] Add Progress Tracking module with RAG status
- [ ] Pilot the tool with a real planning cycle and capture usability feedback

---

*Last updated: 2025-06-12*
*Status: Architecture complete; v1 tool built; extensions pending*
