# Ansible EoA (AAP) — AEP actionability data contract

**Source:** `Ansible EOA - AAP.pdf`  
**Purpose:** Make EoA indicators and Snowflake sources actionable in Adobe Experience Platform (AEP) / RT-CDP B2B for AJO B2B journeys.  
**Status:** Draft contract from indicator dictionary (v0.7 use case)

---

## 1. Population gate (who can be scored / journeyed on telemetry EoA)

An account is in the **AAP EoA model population** only if **all** are true:

1. Active **paid** Ansible Automation Platform subscription (not training/consulting-only; exclude IBM internal / partner noise per query rules)
2. Sending **telemetry within the last 30 days**
3. **Not** an internal or partner account (per population filters)

**Join path (population query):**  
`BOOKINGSMASTER_DB.MARTS.PIPELINE_TRANSACTIONS_ACV` (CRM account)  
→ `ROSETTASTONE_DB.MARTS.MDM_RHSC_EBS_ENHANCED_MAPPING` (CRM ↔ EBS)  
→ `AAPAUTOMATIONANALYTICS_DB.TABLEAU_MARTS.MART_CLUSTER_ANALYTICS` (telemetry active)

**AEP implication:** Build an account audience / batch attribute set only for this population **or** stamp `aap_eoa_in_population = true|false` so AJO can branch telemetry-rich vs proxy journeys.

---

## 2. Identity / grain keys to land in AEP

| Key | Grain | Used by |
|---|---|---|
| `crm_account_id` | Account (RHSC) | Population, sales alerts, buying groups |
| `ebs_account` | Account (EBS) | CES, support cases, Adobe content visits, node counts |
| `org_id` / `rh_org_id` | Automation org | Job explorer, content explorer, Lightspeed |

**AEP requirement:** Account profile must hold CRM + EBS linkage; person journeys still need marketable members on the buying group. Prefer **account attributes** for EoA indicators + **person** for role nurture.

---

## 3. Indicator catalog (actionable attributes)

### Perception

| Indicator | User-facing name | Type / window | Null handling | Snowflake source |
|---|---|---|---|---|
| `customer_effort_score_avg` | Avg. AAP CES | Float 1–5; 180d Ansible cases | Keep NULL | `CXAHUB_DB.MARTS.CUSTOMER_SURVEYS` |
| `customer_effort_score_response_count` | AAP CES Response Count | Integer; 180d | COALESCE 0 | same |
| `cust_esc_case_pct` | AAP Case Escalation Rate (%) | %; 90d | Keep NULL | `EXPERIENCEOPS_DB.CASE_MARTS.SUPPORTCASEINSIGHTS` |

**AJO use:** Low CES (&lt;3) + enough responses → `AAP_PERCEPTION_RISK`. Escalation rate spike → Champion/Decision Maker + CS alert. CES average only trusted when response_count ≥ 2 (dict notes ≥2 for stability; complexity avg requires &gt;2 cases).

### Performance

| Indicator | User-facing name | Type / window | Null handling | Snowflake source |
|---|---|---|---|---|
| `bug_to_case_pct` | AAP Bug-to-Case Ratio (%) | %; 90d | Keep NULL | `SUPPORTCASEINSIGHTS` |
| `sev1_per_100nodes_pct` | Sev1 Cases per 100 Licensed Nodes | normalized; 90d | COALESCE 0 | cases + `MART_TOWER_HOST_METRIC_SUMMARY_MONTHLY` |
| `job_execution_success_pct` | Job Execution Success Percent (%) | %; 30d | Keep NULL | `MART_JOB_EXPLORER` |

**AJO use:** Low job success or high Sev1 density → Performance risk branch (Decision Maker / Champion); distinguish bug friction vs skill gap (pair with proficiency).

### Product usage

| Indicator | User-facing name | Type / window | Null handling | Snowflake source |
|---|---|---|---|---|
| `active_job_templates_count` | Active Job Template Count | Integer; 30d | COALESCE 0 | `MART_JOB_EXPLORER` |
| `licensed_node_count` | Licensed Node Count | Integer; recent month | Keep NULL | host metrics + cluster analytics |
| `job_executions_count` | Job Executions Count | Integer; 30d | COALESCE 0 | `MART_JOB_EXPLORER` |
| `jobs_run_via_workflows_pct` | Jobs Run via Workflows (%) | %; 30d | COALESCE 0 | `MART_JOB_EXPLORER` |
| `lightspeed_activated_flag` | Lightspeed Activated Flag | Boolean; 180d | Keep NULL | `MART_LIGHTSPEED_RECOMMENDATION` |

**AJO use:**  
- Entitled + telemetry population but `job_executions_count = 0` → `AAP_NO_ACTIVATION` / stall  
- Low templates + low executions → usage risk  
- Healthy executions + low workflow % → narrow / scale play  
- Lightspeed flag false → AI accelerator offer lane  

### Proficiency

| Indicator | User-facing name | Type / window | Null handling | Snowflake source |
|---|---|---|---|---|
| `distinct_collections_used_count` | Distinct Collections Used | Integer; 30d | COALESCE 0 | `MART_CONTENT_EXPLORER` |
| `distinct_module_count` | Distinct Module Count | Integer; 30d | COALESCE 0 | `MART_CONTENT_EXPLORER` |
| `role_usage_count` | Role Usage Count | Integer; 30d | COALESCE 0 | `MART_CONTENT_EXPLORER` |
| `lightspeed_suggestions_generated_count` | Lightspeed Suggestions Generated | Integer; 90d | Keep NULL | `MART_LIGHTSPEED_RECOMMENDATION` |
| `lightspeed_suggestion_acceptance_pct` | Lightspeed Acceptance (%) | %; 90d | Keep NULL | same |
| `case_complexity_score_avg` | Avg. AAP Case Complexity (1–5) | Float; 90d; ≥3 cases | Keep NULL | `SUPPORTCASEINSIGHTS` |
| `enablement_content_visit_count` | AAP Enablement Content Visits | Integer; 90d | COALESCE 0 | `ADOBE_DB.MARTS.ADOBE_MRKTNG` |
| `operational_content_visit_count` | AAP Operational Content Visits | Integer; 90d | COALESCE 0 | same |
| `advanced_content_visit_count` | AAP Advanced Content Visits | Integer; 90d | COALESCE 0 | same |

**AJO use:**  
- High enablement visits + long tenure + low jobs → stuck foundational (`AAP_PROFICIENCY_GAP`)  
- Operational/advanced content visits → stage content to maturity  
- Low collections/modules/roles + some jobs → deepen proficiency  
- Lightspeed generated/acceptance → AI engagement nurture  

---

## 4. Snowflake source inventory (ingest targets)

| System / DB.schema.object | Indicators / role |
|---|---|
| `BOOKINGSMASTER_DB.MARTS.PIPELINE_TRANSACTIONS_ACV` | Population (paid AAP sub) |
| `ROSETTASTONE_DB.MARTS.MDM_RHSC_EBS_ENHANCED_MAPPING` | CRM ↔ EBS join |
| `AAPAUTOMATIONANALYTICS_DB.TABLEAU_MARTS.MART_CLUSTER_ANALYTICS` | Telemetry activity; account↔org |
| `AAPAUTOMATIONANALYTICS_DB.TABLEAU_MARTS.MART_JOB_EXPLORER` | Jobs, templates, workflows, success |
| `AAPAUTOMATIONANALYTICS_DB.TABLEAU_MARTS.MART_CONTENT_EXPLORER` | Collections, modules, roles |
| `AAPAUTOMATIONANALYTICS_DB.TABLEAU_MARTS.MART_LIGHTSPEED_RECOMMENDATION` | Lightspeed activation / suggestions |
| `AAPAUTOMATIONANALYTICS_DB.MARTS.MART_TOWER_HOST_METRIC_SUMMARY_MONTHLY` | Licensed nodes |
| `CXAHUB_DB.MARTS.CUSTOMER_SURVEYS` | CES avg + response count |
| `EXPERIENCEOPS_DB.CASE_MARTS.SUPPORTCASEINSIGHTS` | Escalations, bugs, Sev1, case complexity |
| `ADOBE_DB.MARTS.ADOBE_MRKTNG` | Enablement / operational / advanced content visits (`POST_EVAR_63` = EBS; prop 25911) |

---

## 5. Recommended AEP → AJO wiring

1. **Batch / recurring job** (align to EoA monthly cadence where possible): compute indicators in Snowflake → land as **Account** attributes in AEP (or derived dataset → profile).  
2. **Population flag** + raw indicators (do not only land a 1–5 score). Scores help ranking; **indicators** drive branch logic.  
3. **Confidence / null policy:** honor Keep NULL vs COALESCE rules so AJO conditions don’t treat missing CES as “0 effort.”  
4. **Proxy cohort:** accounts with paid AAP but **not** in population (no 30d telemetry) → separate proxy journey (portal/docs/support) until telemetry on.  
5. Map indicators to existing trigger recipes (`AAP_NO_ACTIVATION`, `AAP_USAGE_STALL`, `AAP_LOW_BREADTH`, `AAP_PROFICIENCY_GAP`, `AAP_PERCEPTION_RISK`, `AAP_EXPAND_READY`, `AAP_RENEW_RISK`).

---

## 6. Open DA questions

- Cadence into AEP (daily vs monthly matching EoA)?  
- Org_id → account roll-up rules when multiple orgs map to one CRM account?  
- Exact attribute path / XDM field names in RT-CDP B2B?  
- Who owns the Snowflake → AEP pipeline (DA Lead still TBD)?
