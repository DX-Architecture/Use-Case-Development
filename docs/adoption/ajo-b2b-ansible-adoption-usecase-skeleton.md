# AJO B2B Use Case Skeleton — Ansible Adoption Experience

**Status:** Draft skeleton — **CRM personas / AJO roles drafted (v1)**; GenStudio messaging preferences still open  
**Product / solution interest:** Red Hat Ansible Automation Platform (AAP)  
**Orchestration surface:** Adobe Journey Optimizer B2B Edition (account journeys + buying groups)  
**Primary trigger thesis:** Product usage **or lack of usage** (plus proxy signals while AAP EoA is incomplete) to nurture the right buying-group roles  
**Persona basis:** `crm-title-persona-analysis.md` from adoption-stage + Ansible-opportunity contacts (8,293 title rows) — see §6  
**Sources in `/adoption` (current):** Adoption Framework Primary Deck; Lifecycle selling Value & Adoption (Validate & Propose); *GH_Evidence of Adoption (EoA) Overview*; ALG PNGs — *Why Adoption > Consumption*, *Assessing / Measuring / Dimensions*; *Driving automation adoption + growth*; *Automation Sales Plays*; CRM `Ansible_Customer_Contact_Role.csv`  
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
| Triggers | Usage / non-usage events, inactivity windows, entitlement without activation, proficiency/perception proxies |
| Actions | Role-specific email/SMS, content offers, sales alerts, suppress when high-touch owns the account |
| Exit / handoff | Sales-ready / risk escalation / maturity advance / suppress lists |

### Dependencies

| Dependency | Notes | Status |
|---|---|---|
| AAP EoA model | Monthly account maturity 1–5 across 4Ps | **Blocked — telemetry gaps** (EoA deck) |
| Telemetry-agnostic proxies | Needed for disconnected / low-confidence accounts | Roadmap (CY26) |
| Signal → AEP/RT-CDP B2B | Account + person attributes for journey conditions | TBD — DA |
| Buying group role template | AAP roles + CRM Persona Segment auto-assign (§6) | **v1 drafted** |
| Personas / messaging map | CRM segments → AJO roles locked for planning; GenStudio copy prefs | **Roles: drafted · Messaging: open** |
| Content / offer catalog by stage & role | Labs, learning, CoE, Services, references | Partial (framework + tactics slide) |
| Conflict / frequency rules | vs Marketo AAP nurtures, AGI, ServiceNow playbook | TBD |
| Sales / RHSC alert path | Risk & expansion handoffs; Get-to-Green / ASA for under-usage | Pattern exists (DDP / Sales Assistant / Lifecycle V&A) |
| Telesense / usage review | Ansible (+ OCP/RHEL) usage risk & growth insights for account team | Field-owned; feed proxy triggers where available |

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
- Proxy-first signals until AAP EoA is production-ready
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

## 8. Signal inventory (usage + proxies)

**Constraint:** AAP EoA is **blocked on telemetry gaps** (full model still roadmap). Design journeys with **confidence bands** (EoA: High / Medium / Low) and prefer multi-signal rules. AAP product telemetry default is **enabled (opt-out)** and collects usage/job activity metadata when available.

**EoA vs AREN (do not conflate):** EoA = descriptive 1–5 post-sale adoption maturity on the 4Ps (“how deeply are they realizing value?”). AREN = predictive H/M/L propensity for cross-sell / expand / risk (“what might they buy or churn?”). This AJO use case is **EoA/adoption-first**; AREN may inform prioritization later, not v1 branch logic.

**Design thesis (*Why Adoption > Consumption*):** Consumption-only telemetry is incomplete, unreliable, lacks entitlement context, and creates false under-deployment flags. Orchestrate on **Adoption Maturity** (4Ps), not raw consumption alone. Sustained Product Usage grows when Performance, Proficiency, and Perception advance (*Dimensions of Product Adoption*).

### ALG “Measuring Adoption Maturity” metric ladder
Prioritize **additional** metrics as maturity rises (do not stay stuck on entitlements-only):

| Dimension | 1 Initial | 2 Developing | 3 Operational | 4 Optimizing | 5 Innovator |
|---|---|---|---|---|---|
| **Product Usage** | # entitlements purchased | % subscription units consumed | % active users or teams | % features used in production | % total production workloads |
| **Performance** | # defined KPIs | # tracked KPIs | % KPIs automatically tracked | % improvement on tracked KPIs | % sustained KPI targets (>6 mo) |
| **Proficiency** | % users trained | % trained showing essential tasks | % high proficiency | % teams enabled internally | # self-sufficient teams |
| **Perception** | CES | % increase in perceived value | % rating clear value | # teams advocating internally | # external references / advocacy |

### Product Usage (breadth) — journey mapping
| Signal (working) | Risk example | Expansion example | Confidence if telemetry thin |
|---|---|---|---|
| Activation (installed / first controller activity) | Entitled, never activated | — | Medium with entitlements |
| Consumption (jobs / hosts / capacity) | Flat or decaying activity | Growing consumption | Needs telemetry or proxy |
| Feature usage | Basics only; no advanced features | Advanced / multi-feature | Low until AAP EoA |
| Active users / teams | Single-team automation | Multi-team | Proxy via portal + CRM |
| Age / tenure since purchase | Long tenure + low usage | — | High (subscription data) |

### Performance / Proficiency / Perception (proxies)
| Dimension | Example inputs (EoA + Measuring slide) | Journey use |
|---|---|---|
| Performance | KPIs defined/tracked; update frequency; deployment health; support severity | Stability / value risk → Decision Maker / Champion |
| Proficiency | % trained; essential-task proof; Docs/Portal; support complexity; learning/certs (TBA) | Low proficiency → Practitioner enablement |
| Perception | CES; perceived/clear value; internal/external advocacy | Negative → fix-it; positive → reference/expand |

### v1 “good enough” trigger recipes (proxy-friendly)

| Trigger name | Logic (draft) | Primary roles | Intent |
|---|---|---|---|
| `AAP_NO_ACTIVATION` | Entitled ≥ N days, no activation signal | Practitioner, Champion | Onboard / first value |
| `AAP_USAGE_STALL` | Prior activity, then inactivity ≥ X days | Practitioner, Influencer | Re-engage / unblock |
| `AAP_LOW_BREADTH` | Usage present but single-team / limited feature proxies | Champion, Influencer | Scale adoption |
| `AAP_PROFICIENCY_GAP` | High basic support + low learning engagement | Practitioner | Skills / labs |
| `AAP_PERCEPTION_RISK` | Negative CES / feedback | Champion, Decision Maker | Value proof / CS handoff |
| `AAP_EXPAND_READY` | Healthy usage + engagement + completeness OK | Decision Maker, Champion | Domain / AIOps / integrations |
| `AAP_RENEW_RISK` | Renewal ≤ Y days + low maturity / risk signals | Decision Maker + sales alert | Protect ARR |

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

## 10. AJO configuration checklist (build-ready later)

- [ ] Solution interest: Ansible Automation Platform  
- [ ] Role template + auto-assign filters (title, product interest, Marketo list exclusions)  
- [ ] Completeness thresholds per role  
- [ ] Engagement score weights aligned to adoption (de-emphasize email-only inflation — see existing AJO scoring work)  
- [ ] Account journey graph: entry → wait/listen → role splits → offers → sales alert nodes  
- [ ] Named journey nodes for CJA / reporting  
- [ ] Cap / quiet hours / Marketo concurrency exclusions  
- [ ] Sales alert payload: account, maturity band, trigger, missing roles, recommended play  

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

1. Who owns **DA Lead** and the AAP proxy signal dictionary for AEP?  
2. Is v1 limited to **telemetry-on** accounts, or must we cover low-confidence proxies from day one?  
3. Which existing **AAP Journey Orchestration Playbook** (ServiceNow) assets reuse vs rewrite for general adoption?  
4. When does **Ansible Adoption Progression Guide** / **Ansible EoA data** land (framework “coming soon”)?  
5. Final required role **counts** for completeness = sales-ready (roles themselves are drafted in §6)?  
6. GenStudio messaging preference lock: Ansible PMM + Customer Marketing?  

---

## 13. Suggested next artifacts to add under `/adoption`

| Priority | Artifact | Unlocks |
|---|---|---|
| P0 | AAP signal / proxy dictionary (even draft) | Real trigger definitions |
| P0 | Encode §6 CRM → AJO auto-assign rules in AJO (drop Default/Procurement) | Role template live |
| P1 | GenStudio messaging lock + person-level CRM counts | Copy & GenStudio |
| P1 | Offer/asset list by maturity × role | Journey content nodes |
| P2 | Re-add *Advancing Adoption Maturity* PNG if available (content retained from prior) | Fresher action citations |
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
