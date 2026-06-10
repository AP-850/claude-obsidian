# Tactical resupply drone statement

**User:** Anonymous  
**Created:** 10/16/2025 14:45:22  
**Updated:** 4/13/2026 9:36:53  
**Exported:** 6/2/2026 18:38:15  
**Link:** [https://chatgpt.com/c/68f0ccb4-0380-8323-8c55-5fedbd2ef32e](https://chatgpt.com/c/68f0ccb4-0380-8323-8c55-5fedbd2ef32e)  

## Prompt:
16/10/2025, 14:45:22

Provide a capability need statement for a tactical resupply drone

## Response:
16/10/2025, 14:45:25

# Capability Need Statement — Tactical Resupply Drone

## 1. Title
Tactical Resupply Uncrewed Aerial System (TR-UAS)

## 2. Capability Need Summary
A reliable, survivable, and easily deployable tactical resupply drone to deliver critical supplies (ammunition, medical aid, batteries, sensors, specialist spares) from unit-level logistics nodes to dispersed combat elements in austere desert and littoral environments. The system must increase sustainment reach, reduce ground convoy risk, shorten resupply timelines, and enable continuous operations in degraded or contested environments.

## 3. Operational Problem
Ground resupply in expeditionary/desert operations is slow, exposes convoys to ambush/IED threat, and is constrained by terrain, restricted lines-of-communication, and weather (dust storms, high heat). Small units operating beyond line-of-sight or inside complex terrain (urban edges, canyons, wadis) require rapid, on-demand delivery of small-to-medium payloads to maintain tempo and reduce mission aborts. Existing heavy rotary/wing resupply assets are inefficient for frequent, low-volume tactical deliveries.

## 4. Desired Operational Effects
- Reduce time-to-resupply for frontline teams from hours to minutes.
- Reduce exposed personnel and vehicle risk by enabling remote resupply.
- Increase mission endurance (sustainment of combat effect) without additional ground logistics tail.
- Provide precision delivery to pre-coordinated or ad-hoc drop points with minimal manpower overhead.

## 5. Key Employment Concepts
- Unit-level request → launched from forward arming/refuel/logistics node or vehicle → autonomous or supervised flight → precision delivery (soft-drop, winch/retract, or landing) → return-to-base or expendable options.
- Rapid re-tasking via secure datalink to support dynamic battlefields.
- Integration with SAT/mission planning tools and force C2 for tasking and deconfliction.

## 6. Minimum Mandatory Requirements (Threshold)
These are non-negotiable for initial fielding.
- **Payload:** 10 kg net usable payload (modular cargo pods).  
- **Range:** 20 km one-way (40 km round trip) with payload under typical desert conditions.  
- **Endurance:** ≥30 minutes with 10 kg payload (cruise).  
- **Cruise Speed:** ≥70 km/h; max speed ≥100 km/h.  
- **Delivery Modes:** At least two: precision soft-drop (GPS-guided) and winch delivery to stationary or stationary-moving recipients.  
- **Navigation:** GNSS with inertial navigation backup and terrain/vision-aided navigation for GPS-denied environments.  
- **Datalink:** Encrypted, anti-jam capable beyond-line-of-sight (BLOS) or LOS with relay option.  
- **Environmental Tolerance:** Operate in +50°C ambient, sand/dust ingestion tolerance, wind up to 30 km/h sustained, and survival through short-duration dust storms.  
- **Launch/Recovery:** Vehicle/van/flat-packable launch & rapid deployable recovery options; no requirement for prepared runway.  
- **Operator Requirement:** Crew of ≤2 trained operators for routine operations; single-operator mission control for common profiles.  
- **Logistics:** Ground deployable ground support equipment (GSE) that fits within tactical vehicles (e.g., Land Cruiser / MRZR / Polaris MRZR footprint).  
- **Safety/Standards:** Fail-safe return-to-home (RTH), safe descent in failure modes, and compliance with applicable airspace and safety rules for military operations.

## 7. Desired Capabilities (Objective)
- **Payload:** 20 kg payload option (modular).  
- **Range/Endurance:** 50 km one-way / ≥90 minutes endurance with smaller payloads.  
- **Autonomy:** High autonomy: automated replan, obstacle avoidance, dynamic routing, multi-aircraft swarm logistics coordination.  
- **Survivability:** Low-observable signature, radar cross-section reduction, and counter-EW resilience.  
- **Rapid Reload:** Ground reload/re-arm cycle ≤10 minutes with minimal tooling.  
- **Hot & Cold Weather:** Operability down to -10°C and up to +55°C.  
- **Interoperability:** Standardized interfaces for integration with unit mission planning tools, C2, and logistics trackers (APIs).  
- **Modularity:** Plug-and-play pods for medevac (small casualty extraction), ISR sensors, fuel cell/battery recharge capsule.  
- **Precision Landing:** Autonomous vertical landing on small prepared pads or vehicle decks.  
- **Night Ops:** Full night capability with IR/lidar aiding.  
- **Safety:** Parachute for airframe in catastrophic failure.

## 8. Constraints & Assumptions
- System will operate primarily in austere desert/littoral environments with limited forward maintenance infrastructure.  
- Airspace will be contested with potential GPS degradation and limited BLOS datalink support; measures for resilience assumed.  
- Budget and manpower limitations favor small, modular systems over large, platform-specific solutions.

## 9. Measures of Effectiveness (MoE)
- **Time-to-delivery:** % of requests delivered within target time (e.g., ≤20 minutes for point-to-point ≤10 km).  
- **Mission success rate:** % of sorties that deliver cargo within acceptable tolerance.  
- **Sortie rate:** Average deliveries per launch node per 24 hours.  
- **Risk reduction:** Reduction in convoy exposure hours / reduction in ground resupply vehicle km.  
- **Logistics cost-per-kg:** Comparative metric against ground convoy and manned rotary lift.  
- **Availability:** Mission-capable rate (≥85% target).

## 10. Acceptance Criteria / Key Performance Parameters (KPPs)
- Demonstrated delivery of 10 kg to a 5 m x 5 m target from 20 km range in operational environmental conditions in at least 10 consecutive sorties.  
- Return-to-base or controlled recovery in >95% of non-catastrophic failure sorties.  
- Reload/recycle time ≤15 minutes under field conditions.  
- Operator training requirement ≤ 40 hours initial plus standard recurrent currency.  
- Ability to integrate with unit C2 and logistics tracking APIs.

## 11. Training & Personnel
- Operator course (initial): theory, practical launch/recovery, emergency procedures, EW/GPS denial drills — target ≤40 hours.  
- Maintainer course: Level-1 field repair & module swaps — target ≤24 hours.  
- Minimal additional manpower: capable of being fielded by existing logistics elements with modest additional manpower.

## 12. Sustainment & Logistics Support
- Common modular spare parts, swappable batteries/power units, and depot-level repair plan.  
- Field support package sized to support a six-airframe squadron for 30 days.  
- Battery/energy supply consideration for hot climates and fast recharge/replace options.

## 13. Safety, Legal & Regulatory Considerations
- Compliance with applicable national/military airspace regulations and local airspace coordination procedures.  
- Clear rules of engagement for operations in contested/denied environments, including propagation of loss-of-control and ordnance-free payload rules.  
- Biomedical handling SOPs for medical payloads (if used).

## 14. Risk Assessment (Top Risks)
- **Electronic warfare (EW):** GPS/datalink jamming causing mission failure. Mitigation: inertial nav, anti-jam datalinks, preprogrammed fail-safes.  
- **Environmental wear:** Sand ingestion, thermal stress reducing MTBF. Mitigation: hardened filters, thermal management.  
- **Logistics tail:** Battery/pod resupply complexity. Mitigation: modular swappable packs and standardized batteries.  
- **Airspace deconfliction** with manned aviation. Mitigation: integrated C2, defined corridors and procedures.

## 15. Prioritization for Acquisition
1. **Survivable navigation & resilient datalink** (mandatory).  
2. **10 kg payload, 20 km range, reliable precision delivery modes** (mandatory).  
3. **Rapid reload & simple field maintenance** (mandatory).  
4. **Improved range/payload/autonomy options** (objective for later blocks).  

## 16. Incremental Development & Fielding Path
- **Block 0 (Proof of Concept):** 10 kg payload, 20 km range, basic GPS/INS navigation, soft-drop, manual operator control, deployable from trucks.  
- **Block 1 (Initial Operational Capability):** Hardened against dust/heat, anti-jam datalink, winch delivery, operator/maintainer courses.  
- **Block 2 (Full Capability):** Enhanced autonomy, swarm logistics, 20–50 kg scalable pods, precision landing and medevac option.

---

If you want, I can convert this into a one-page brief for senior leadership (PPT slide) with a short recommended acquisition approach and a draft cost/benefit snapshot tailored to desert operations. Which format do you prefer?

## Prompt:
16/10/2025, 14:49:28

Please provide a short paragraph on concept of employment

## Response:
16/10/2025, 14:49:34

The tactical resupply drone is employed as a front-line logistics multiplier: unit-level requests are queued through local C2 or a logistics node, a nearby launcher (vehicle, trailer or portable rack) dispatches an autonomous or supervised sortie, and the drone conducts a low-signature, GPS/INS-guided approach to deliver modular cargo via soft-drop, winch, or precision landing. Missions are taskable on-demand or pre-planned for routine sustainment, with secure datalink re-tasking to support shifting tactics and emergency casualties. Deconfliction with manned air assets, EW-resilient navigation modes, and fail-safe recovery behaviours (RTH, controlled descent) ensure resilience in contested or GPS-denied environments, while rapid reload and simple field maintenance keep the system cycling to sustain tempo without increasing the ground logistics footprint.



---
Powered by [ChatGPT Exporter](https://www.chatgptexporter.com)