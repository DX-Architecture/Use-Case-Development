# AJO B2B Use Case Skeleton — Ansible Adoption Experience

**Status:** Draft skeleton — **CRM personas / AJO roles drafted (v1)**; GenStudio messaging preferences still open  
**Product / solution interest:** Red Hat Ansible Automation Platform (AAP)  
**Orchestration surface:** Adobe Journey Optimizer B2B Edition (account journeys + buying groups)  
**Primary trigger thesis:** Product usage **or lack of usage** using **Ansible EoA AAP indicators** landed in AEP (plus proxy path when outside telemetry population) to nurture buying-group roles  
**Persona basis:** `crm-title-persona-analysis.md` from adoption-stage + Ansible-opportunity contacts (8,293 title rows) — see §6  
**Sources in `/adoption` (current):** *Ansible EOA - AAP.pdf* (indicator dictionary + Snowflake sources); Adoption Framework Primary Deck; Lifecycle selling Value & Adoption (Validate & Propose); *GH_Evidence of Adoption (EoA) Overview*; ALG PNGs; *Driving automation adoption + growth*; *Automation Sales Plays*; CRM `Ansible_Customer_Contact_Role.csv`  
**AEP data contract:** `ansible-eoa-aap-aep-data-contract.md` (derived from Ansible EOA - AAP)  
**Sources retained from prior ingest (files not currently in folder):** Advancing Adoption Maturity action matrix  
**Related contacts (from decks):** Ansible BU — Tricia McConnell; Adoption Framework — Corinne Russo / Britni Coble; EoA — Bianca Gallina; Experiences & Signals — Jay Hall  

---

## 1. Why / What / How / Dependencies / DA Lead

### Why
Customers buy AAP but do not consistently progress from entitlement → active automation → multi-team / multi-use-case value. **Customer reality:** automation adoption at scale is still hindered by time, resource, and skill constraints. Fragmented consumption metrics alone mislead (telemetry gaps, no entitlement context, false under-deployment). Without role-aware nurture, Marketing over-messages practitioners, under-enables champions, and Sales/CS miss risk and expansion moments.

**Business play (Ansible):** Make AAP stickier, drive renewals, and protect/grow the AAP base with focused migration to **AAP 2.6**, while advancing accessibility, intelligence, and impact (automation dashboard, portal, execution environment builder, cloud/HashiCorp integrations).

### What
An **always-on AJO B2B account journey** for entitled AAP accounts that:

1. Builds / refreshes an **AAP solution-interest buying group** with required roles.
2. Classifies the account on **adoption maturity** (Initial → Innovator) using available **usage + proxy signals**.
3. Branches nurture and sales alerts by **maturity gap** and **role** (usage risk vs expansion readiness).
4. Measures impact via engagement, completeness, maturity movement, and renewal/expansion outcomes.

### How (AJO B2B pattern)

| Layer | Approach |
|---|---|
| Unit of orchestration | **Account** (not person-only) |
| Solution interest | Ansible Automation Platform |
| Membership | Buying group role template + auto-assign rules |
| Readiness | Completeness score + engagement score + maturity/proxy band |
| Triggers | EoA indicators in AEP (jobs, templates, CES, Sev1, content depth, etc.) + proxy when out of telemetry population |
| Actions | Role-specific email/SMS, content offers, sales alerts, suppress when high-touch owns the account |
| Exit / handoff | Sales-ready / risk escalation / maturity advance / suppress lists |

### Dependencies

| Dependency | Notes | Status |
|---|---|---|
| AAP EoA indicator dictionary | Named metrics + Snowflake queries (*Ansible EOA - AAP.pdf*) | **Available — land in AEP** |
| AAP EoA aggregate 1–5 score | Monthly maturity score across 4Ps | Confirm publish cadence / feed |
| Telemetry-on population gate | Paid AAP + telemetry ≤30d + not internal/partner | Required for telemetry branches |
| Signal → AEP/RT-CDP B2B | Account attributes from §8 / data contract | **P0 — DA** |
| Buying group role template | AAP roles + CRM Persona Segment auto-assign (§6) | **v1 drafted** |
| Personas / messaging map | CRM segments → AJO roles locked for planning; GenStudio copy prefs | **Roles: drafted · Messaging: open** |
| Content / offer catalog by stage & role | Labs, learning, CoE, Services, references; Adobe BOM topics in EoA notes | Partial |
| Conflict / frequency rules | vs Marketo AAP nurtures, AGI, ServiceNow playbook | TBD |
| Sales / RHSC alert path | Risk & expansion handoffs; Get-to-Green / ASA for under-usage | Pattern exists (DDP / Sales Assistant / Lifecycle V&A) |
| Telesense / usage review | Ansible usage risk & growth for account team | Field-owned; align to same indicators where possible |

### DA Lead
**TBD** — assign Analytics / AEP owner for signal schema, confidence bands, and journey-eligible audiences.

---

## 2. Business outcomes

| Outcome | Working definition |
|---|---|
| Faster time-to-value | Move accounts from Initial/Developing → Operational on usage + proficiency proxies |
| Protect renewal | Detect “quiet but stuck” accounts (low usage / high basic support / poor sentiment) before renewal window |
| Expand responsibly | Surface expansion only when usage breadth + perception support it (not volume spam) |
| Role coverage | Raise buying-group completeness for required AAP roles |
| Coordinated motion | Digital (AJO) + high-touch (Tech Sales / CS) share the same maturity language |

---

## 3. Scope

### In scope (v1 skeleton)
- Post-sale / entitled AAP accounts (Adopt focus; Onboard and Renew as adjacent stages)
- Account journey with role-aware branches for **usage risk** and **healthy usage / expand**
- **AEP-actionable** Ansible EoA AAP indicators + Snowflake sources (§8 / data contract); proxy path for out-of-population accounts
- CRM-derived AJO roles + GenStudio persona bridge (§6); creative production still open

### Out of scope (v1)
- Net-new acquire / Learn-only journeys
- Full AAP EoA-dependent branching (design for, do not block on)
- In-app Intercom/Amplitude orchestration (adjacent channel; not AJO B2B core)
- Final GenStudio creative / brand-locked messaging production

---

## 4. Lifecycle alignment

Adoption Framework spine: **Learn → Onboard → Adopt → Expand → Renew**

**Lifecycle selling overlay (Value & Adoption | Validate & Propose):** Quarterly motion starting ~Day 90. Desired outcome: customer has deployed/adopted AAP **or** has a feasible plan. Field path explicitly calls for reviewing **digital nurture / telemetry signals** (ALG) and assessing **adoption risk** (Adoption Framework → Get-to-Green as needed). Under-usage findings hand to ASA; growth via ALG maturity matrix + Propose-stage cross-sell/upsell.

| Lifecycle stage | AJO job for this use case | Maturity focus (ALG / EoA) |
|---|---|---|
| Onboard | Confirm activation; first successful automation milestone | 1 Initial → 2 Developing |
| Adopt | Deepen usage across teams/features; raise proficiency | 2 → 3 Operational |
| Expand | Multi-domain / platform breadth when ready | 3 → 4 Optimizing |
| Renew | Risk remediation + value proof for economic buyers | Any; prioritize low maturity + near renewal |

**v1 primary stage:** Adopt (with Onboard entry and Renew-risk side door), aligned to Validate (usage/risk review) then Propose (expansion) selling path.

**Field tools to mirror in alerts / air cover (not AJO-owned):** Telesense (Ansible usage risk/growth), Pitchbuilder value reinforcement, RHSC contact/MEDDPICC updates, Consulting/Training/TAM when proficiency gaps persist.

---

## 5. Buying group — roles (CRM-informed v1)

AJO B2B solution interest: **Red Hat Ansible Automation Platform**

Roles below are the **v1 proposed buying-group template**, mapped from CRM Persona Segments in `crm-title-persona-analysis.md` (adoption-stage + Ansible opportunity members). Completeness defaults to ≥1 member per required role unless Sales defines otherwise.

| AJO role | Required? (v1) | Primary CRM Persona Segments | Job in adoption journey |
|---|---|---|---|
| **Practitioner** | Yes | System Administrator, Developer, Platform Engineer, Network Admin / Ops, SRE, Data Scientist IC, IT Security / Compliance (~20% opp wt) | Operate AAP day-to-day; first jobs → advanced automation |
| **Champion** | Yes | **AppDev ITDM** (largest named segment, ~22%), IT Operations Leader, Line of Business (~23% combined) | Internal advocate; drives multi-team adoption |
| **Influencer** | Yes | Enterprise Architect, Network Architect, Automation Architects (~8%) | Architecture / standards; expands use cases |
| **Decision Maker** | Yes (Expand / Renew) | IT C-Suite, C-Suite (~12%) | Budget, renewal, expansion |
| **Executive Steering Committee** | No (v1) | — | Optional for large enterprise |
| **Other / Exclude** | Catch-all | **Default** (~31%), Procurement (~1.7%) | Do not primary-nurture / do not auto-assign |

### Role × 4P ownership (working heuristic)

| Dimension | Primary roles to nurture | Secondary |
|---|---|---|
| **Product Usage** | Practitioner, Influencer | Champion |
| **Proficiency** | Practitioner | Champion (peer enablement) |
| **Performance** | Decision Maker, Champion | Influencer |
| **Perception** | Champion, Decision Maker | Influencer |

---

## 6. Personas & titles (from CRM analysis)

### Status — drafted for AJO membership
**CRM personas are no longer TBD for role assignment.** Source: `Ansible_Customer_Contact_Role.csv` → `crm-title-persona-analysis.md`  
Filter: adoption-stage Ansible customers who are members of an Ansible opportunity (**8,293** title rows · ~**46k** opportunity-weight).

| Layer | Status | What it unlocks |
|---|---|---|
| **CRM Persona Segments → AJO roles** | **v1 drafted** | Buying-group auto-assign, completeness, journey role splits |
| **GenStudio messaging preferences** | **Still open** | Email/copy tone per persona (PMM lock) |
| **Person-level CRM counts** | Open | Validate title uniqueness vs unique contacts |

Named segments cover ~**69%** of opportunity weight. **AppDev ITDM** is the dominant Champion signal. **Default (~31%)** and **Procurement** are excluded from v1 auto-assign.

### CRM → AJO role map (v1)

| AJO role | Include Persona Segments | ~Opp weight | Notes |
|---|---|---:|---|
| **Practitioner** | System Administrator, Developer, Platform Engineer, Network Admin / Ops, SRE, Data Scientist IC, IT Security / Compliance | ~20% | Mostly IC / Default seniority; Managers in these segments may dual-map to Champion |
| **Influencer** | Enterprise Architect, Network Architect, Automation Architects | ~8% | Reinforce with title keywords (`Architect`, `Automation`, `AIOps`) |
| **Champion** | AppDev ITDM, IT Operations Leader, Line of Business | ~23% | AppDev ITDM is Manager (~46%) / Director (~30%)-heavy |
| **Decision Maker** | IT C-Suite, C-Suite | ~12% | CXO / XVP / Director-heavy; Expand + Renew |
| **Exclude / Other** | Procurement; Persona Segment = **Default** | ~32% | Default too noisy for auto-assign; Procurement ≠ adoption nurture |

**Hold for review (do not auto-map yet):**
- **Business Analyst (~4%)** — many sourcing/consulting titles; not a clean Champion signal.
- **Automation Architects** — thematically right; reinforce with keywords (some misfiles).
- **Developer** — Practitioner for IC titles; combine segment + keywords (managers/VPs appear in segment).

### Top named segments (by opportunity weight)

| Rank | Persona Segment | Opp share | Primary AJO role |
|---|---|---:|---|
| 1 | AppDev ITDM | 22.0% | Champion |
| 2 | IT C-Suite | 9.5% | Decision Maker |
| 3 | System Administrator | 9.2% | Practitioner |
| 4 | Developer | 8.3% | Practitioner |
| 5 | Enterprise Architect | 5.1% | Influencer |
| — | Default (unclassified) | 30.6% | Exclude from auto-assign |

### GenStudio persona bridge (for copy Parameters)

| GenStudio persona | Primary CRM segments | AJO roles | Messaging status |
|---|---|---|---|
| Champion | AppDev ITDM, IT Operations Leader, Line of Business | Champion | Preferences open — use GenStudio Champion guidelines interim |
| Technical Practitioner / Architect | SysAdmin, Platform Eng, SRE, Network Admin/Ops, Enterprise / Network / Automation Architects | Practitioner, Influencer | Preferences open — use GenStudio TP/Architect guidelines interim |
| Developer | Developer (IC titles) | Practitioner | Preferences open — IC-only; avoid manager/VP titles |

### Remaining validation steps
1. Person-level counts (not only unique titles) for mapped segments.
2. Title-keyword overlays + sample reclassify 50 Default titles.
3. Tech Sales completeness workshop (required role counts).
4. Confirm Business Analyst and Automation Architects segment quality.
5. Lock GenStudio messaging preferences per persona after PMM review.

---

## 7. Entry, branch, and exit logic

### Entry (account qualifies when)
Working draft — finalize with DA:

- Account has **AAP entitlement / subscription** active, **and**
- Solution interest = AAP buying group exists or can be created, **and**
- At least one marketable member in a required role **or** completeness play is allowed to recruit missing roles, **and**
- Not on global suppress / competing exclusive journey (TBD).

### Primary branches

```
Account enters (entitled AAP)
 ├─ Missing required roles → Completeness / role-recruitment play
 ├─ Usage RISK (entitled + low/no usage OR stalled inactivity)
 │    ├─ Practitioner / Influencer → Proficiency + first-value nurture
 │    └─ Champion / Decision Maker → Risk narrative + enablement / Services CTA
 ├─ Usage HEALTHY but narrow (single team / limited features)
 │    └─ Influencer / Champion → “Automate at scale” / CoE / reuse patterns
 ├─ Usage HEALTHY + expansion signals
 │    └─ Decision Maker / Champion → Expand offers (domain, AIOps, integrations)
 └─ Near renewal + low maturity → Renew-risk play + sales alert
```

### Exit / suppress (draft)
- Maturity band advances past journey objective (e.g. sustained Operational+)
- Sales/CS owns active high-touch adoption task (suppress digital or switch to air cover only)
- Opt-down / unsubscribe / legal suppress
- Account loses AAP entitlement
- Frequency / conflict caps hit

---

## 8. Signal inventory & AEP actionability (Ansible EoA AAP)

**Source of truth for metrics:** `Ansible EOA - AAP.pdf` → working contract `ansible-eoa-aap-aep-data-contract.md`.  
These **named indicators** (not only a 1–5 score) must be landed as **account attributes in AEP / RT-CDP B2B** so AJO can branch on them.

### Population gate (telemetry EoA cohort)
Eligible only if: **active paid AAP subscription** AND **telemetry in last 30 days** AND **not internal/partner**.  
Keys: `crm_account_id` ↔ `ebs_account` (Rosetta) ↔ `org_id` (Automation Analytics).  
Accounts with entitlement but **outside** population → **proxy / disconnected** journey until telemetry is on.

### AEP ingest — Snowflake sources to make actionable

| Source | What it feeds |
|---|---|
| `BOOKINGSMASTER_DB.MARTS.PIPELINE_TRANSACTIONS_ACV` | Paid AAP population |
| `ROSETTASTONE_DB.MARTS.MDM_RHSC_EBS_ENHANCED_MAPPING` | CRM ↔ EBS join |
| `AAPAUTOMATIONANALYTICS_DB.TABLEAU_MARTS.MART_CLUSTER_ANALYTICS` | Telemetry activity; account↔org |
| `…MART_JOB_EXPLORER` | Job volume, templates, workflows, success rate |
| `…MART_CONTENT_EXPLORER` | Collections, modules, roles (proficiency depth) |
| `…MART_LIGHTSPEED_RECOMMENDATION` | Lightspeed activation / suggestions / acceptance |
| `…MART_TOWER_HOST_METRIC_SUMMARY_MONTHLY` | Licensed node footprint |
| `CXAHUB_DB.MARTS.CUSTOMER_SURVEYS` | Ansible CES avg + response count |
| `EXPERIENCEOPS_DB.CASE_MARTS.SUPPORTCASEINSIGHTS` | Escalations, bugs, Sev1, case complexity |
| `ADOBE_DB.MARTS.ADOBE_MRKTNG` | Enablement / operational / advanced content visits |

### Indicator → journey mapping (v1)

| Dimension | Indicators (attribute names) | AJO / AEP action |
|---|---|---|
| **Product usage** | `job_executions_count`, `active_job_templates_count`, `licensed_node_count`, `jobs_run_via_workflows_pct`, `lightspeed_activated_flag` | Zero/low jobs or templates → activation/stall; low workflow % with volume → scale/breadth; Lightspeed off → AI accelerator |
| **Performance** | `job_execution_success_pct`, `bug_to_case_pct`, `sev1_per_100nodes_pct` | Low success / high Sev1 density → stability risk (Decision Maker / Champion) |
| **Proficiency** | `distinct_collections_used_count`, `distinct_module_count`, `role_usage_count`, Lightspeed suggestion metrics, `case_complexity_score_avg`, `enablement_content_visit_count`, `operational_content_visit_count`, `advanced_content_visit_count` | Low craft metrics → Practitioner enablement; foundational content + weak usage → stuck; advanced content → EDA / AIOps offers |
| **Perception** | `customer_effort_score_avg`, `customer_effort_score_response_count`, `cust_esc_case_pct` | Low CES (with enough responses) or escalation spike → perception risk / CS handoff |

**Null policy:** Honor Keep NULL vs COALESCE-to-0 from the dictionary (do not treat missing CES as 0). Case complexity average only when ≥3 cases in window.

**EoA vs AREN:** EoA = descriptive value realization (this section). AREN = predictive buy/expand/risk — do not conflate for v1 branch logic.

### ALG Measuring ladder (planning overlay)
Retain the 1–5 Measuring Adoption Maturity narrative; **wire AJO conditions to the named indicators above** once they exist in AEP.

### v1 trigger recipes (bound to EoA indicators)

| Trigger name | Logic (draft — AEP attributes) | Primary roles | Intent |
|---|---|---|---|
| `AAP_OUT_OF_POPULATION` | Paid AAP but not in 30d-telemetry population | Champion, Practitioner | Proxy enablement; drive telemetry on |
| `AAP_NO_ACTIVATION` | In population; `job_executions_count` / templates ≈ 0 | Practitioner, Champion | First value / onboarding |
| `AAP_USAGE_STALL` | Prior jobs &gt; 0; recent executions flat/zero | Practitioner, Influencer | Re-engage / unblock |
| `AAP_LOW_BREADTH` | Jobs present; low templates and/or workflow % / collections | Champion, Influencer | Scale / CoE / reuse |
| `AAP_PROFICIENCY_GAP` | Low modules/roles/collections **or** high enablement visits + weak usage | Practitioner | Skills / labs / operational content |
| `AAP_PERFORMANCE_RISK` | Low job success and/or high Sev1 density / bug-to-case | Decision Maker, Champion | Stability / Services |
| `AAP_PERCEPTION_RISK` | CES &lt; 3 with adequate responses **or** high escalation % | Champion, Decision Maker | Value proof / CS handoff |
| `AAP_EXPAND_READY` | Healthy jobs + templates + workflows/collections; perception OK; completeness OK | Decision Maker, Champion | Domain / EDA / AIOps / Lightspeed |
| `AAP_RENEW_RISK` | Renewal ≤ Y days + usage/performance/perception risk | Decision Maker + sales alert | Protect ARR |

---

## 9. Role × maturity action matrix (content TBD)

Actions drawn from ALG “Advancing Adoption Maturity” + Automation sales tactics. Replace asset names when catalog is mapped.

| Maturity | Practitioner | Champion | Influencer | Decision Maker |
|---|---|---|---|---|
| **1 Initial** | First use case pilot; onboarding; essentials training | Awareness + early-win kit | Identify key teams / use cases | Define KPIs / business value framing |
| **2 Developing** | Essential tasks; standardize configs | Internal value storytelling | Expand across teams | Track KPIs; Services if stuck |
| **3 Operational** | Advanced features; automate deployments | Peer advocacy; track sentiment | Integrations (ITSM, obs, Win, etc.) | Efficiency KPI outcomes |
| **4 Optimizing** | Expert paths; production workload depth | CoE / community of practice | Embed in business strategy | Sustain KPI targets; expand domains |
| **5 Innovator** | Emerging capabilities; latest releases | External advocacy / references | Thought leadership / best practices | Industry leadership narrative |

### Use-case / sales-play lanes (content targeting)
AAP is the **Automation TDP** — a consistent automation layer across the Red Hat portfolio and a path to AI-driven operations. Map nurture offers to these plays (*Automation across the sales plays*):

| Sales play | Role emphasis | Example offer themes | Priority for v1 |
|---|---|---|---|
| **IT Operations Efficiency** | Practitioner, Champion | Reduce toil; automated remediation; standardize to cut drift/downtime; EDA for real-time ops; generative AI to simplify admin / create automation | **Primary** |
| **AI-Ready Enterprise** | Influencer, Decision Maker | EDA for AIOps; policy-as-code; AI model lifecycle automation; observability → remediation | Secondary |
| **Build and Run Apps** | Practitioner, Influencer | Consistent RHEL/OpenShift environments; deploy + config mgmt; DevOps / platform pipeline automation; multi-cloud | Secondary |
| **Sovereignty** | Decision Maker, Influencer | Policy compliance; hybrid governance; open standards; sovereign control; auditable ops | Selective |

**Platform adoption accelerators** (*Driving automation adoption + growth*): automation dashboard (intelligence), automation portal (new automators), execution environment builder (governance), HashiCorp / Ansible on Cloud / streamlined install + **AAP 2.6 migration**.

Actions in the maturity matrix below still draw from ALG Advancing Adoption Maturity where asset names are TBD.

---

## 10. AJO / AEP configuration checklist

- [ ] **AEP:** Land population flag + EoA indicator attributes on Account (see data contract)  
- [ ] **AEP:** CRM ↔ EBS ↔ org_id identity stitching validated  
- [ ] Solution interest: Ansible Automation Platform  
- [ ] Role template + auto-assign filters (title, product interest, Marketo list exclusions)  
- [ ] Completeness thresholds per role  
- [ ] Engagement score weights aligned to adoption (de-emphasize email-only inflation)  
- [ ] Account journey graph: population split → indicator triggers → role splits → offers → sales alerts  
- [ ] Named journey nodes for CJA / reporting  
- [ ] Cap / quiet hours / Marketo concurrency exclusions  
- [ ] Sales alert payload: account, indicators firing, trigger, missing roles, recommended play  

---

## 11. Success metrics

| Layer | Metric |
|---|---|
| Orchestration | Buying-group completeness; % accounts with required roles; journey enter/exit |
| Engagement | Role-level email engagement; content completion (labs/learning) |
| Adoption | Proxy or EoA maturity movement (e.g. % L1/L2 → L3 in 90 days) |
| Revenue | Renewal retention on nurtured risk accounts; expansion opptys influenced (pattern: SNow pilot tracked opptys/$ ) |
| Coordination | % risk triggers with sales task created; digital suppress when high-touch active |

---

## 12. Open questions

1. Who owns **DA Lead** for Snowflake → AEP landing of the Ansible EoA indicator set?  
2. Cadence into AEP (daily vs monthly EoA recompute)?  
3. How to roll up multiple `org_id`s to one `crm_account_id` for journey decisions?  
4. Exact XDM / account attribute names in RT-CDP B2B?  
5. Is v1 limited to **in-population** accounts first, with proxy cohort phase-2?  
6. Which **AAP Journey Orchestration Playbook** (ServiceNow) assets reuse vs rewrite?  
7. Final required role **counts** for completeness = sales-ready?  
8. GenStudio messaging preference lock: Ansible PMM + Customer Marketing?  

---

## 13. Suggested next artifacts to add under `/adoption`

| Priority | Artifact | Unlocks |
|---|---|---|
| P0 | AEP mapping sheet (indicator → XDM field → AJO condition) | Build-ready journeys |
| P0 | Encode §6 CRM → AJO auto-assign rules in AJO | Role template live |
| P1 | Threshold recommendations per trigger (with DA / EoA owners) | Non-noisy branching |
| P1 | GenStudio messaging lock + person-level CRM counts | Copy & GenStudio |
| P1 | Offer/asset list by maturity × role (tie to Adobe BOM topics in EoA notes) | Journey content nodes |
| P2 | Ansible Adoption Progression Guide | Milestone language |
| P2 | Conflict matrix vs Marketo / AGI / SNow | Safe always-on execution |

---

## Document control

| Version | Date | Notes |
|---|---|---|
| 0.1 | 2026-10-01 | Skeleton from Adoption Framework + EoA + ALG screenshots; personas TBD |
| 0.2 | 2026-10-01 | CRM title/persona CSV ingested; §6 role map drafted; messaging personas still TBD |
| 0.3 | 2026-10-01 | Lifecycle selling Value & Adoption (Validate & Propose) overlay; sync rule/manifest/hook added |
| 0.4 | 2026-10-01 | Source rename sync: ALG PNGs; Measuring metric ladder added; EoA PDF + old screenshots removed from folder (concepts retained) |
| 0.5 | 2026-10-01 | Ingest *Driving automation adoption + growth*, *Automation Sales Plays*, *GH_EoA Overview*; AAP 2.6 / sales-play lanes; EoA vs AREN |
| 0.6 | 2026-10-01 | Promote CRM persona findings from TBD → v1 drafted AJO roles; messaging prefs remain open |
| 0.6.1 | 2026-10-02 | Shareable HTML/PDF exports added; classified as deliverables (not research sources) in sync manifest |
| 0.7 | 2026-10-02 | Ingest *Ansible EOA - AAP.pdf*; AEP data contract; indicator→trigger mapping; Snowflake source inventory |

### Shareable exports
- `AJO-B2B-Ansible-Adoption-Use-Case-Shareable.html` — print-ready HTML for browser viewing
- `AJO-B2B-Ansible-Adoption-Use-Case.pdf` — email-friendly PDF export of this skeleton  
Regenerate these when the skeleton changes materially. They are **outputs**, not inputs to the use case.

### Supporting analysis
- `ansible-eoa-aap-aep-data-contract.md` — full indicator catalog, null rules, and AEP wiring notes from *Ansible EOA - AAP.pdf*
