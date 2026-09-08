# Call Center Operations Performance Analysis

Operational KPI analysis of call-center activity, focused on service reporting, operator-level review, volume-aware interpretation, and practical decision support.

## Quick Access

- [Analysis notebook](Call_Center_Operator_Performance_Analysis.ipynb)
- [Operator KPI output](outputs/operator_kpis.csv)
- [Weekly system KPI output](outputs/system_week_kpis.csv)
- [Missed-call concentration output](outputs/operator_missed_call_pareto.csv)

## Executive Summary

This project analyzes virtual-telephony activity to understand inbound service performance and provide an operator-review framework without reducing employee performance to one unsupported binary label.

After removing 4,900 exact duplicates from 53,902 source records, the operator-assigned analytical population represented:

- **93,802 inbound calls**, including **926 missed calls**;
- a **0.99% missed inbound rate** within the operator-assigned population;
- a **13.15-second call-weighted average inbound wait**;
- **608,343 outbound calls**, analyzed separately as descriptive activity.

Missed-call impact was moderately concentrated: **27 operators accounted for 50%** of operator-assigned missed calls, while **92 accounted for 80%**. This showed why missed-call rate, absolute missed calls, and call volume need to be reviewed together.

## Business Problem

Call-center supervisors need reporting that distinguishes system-level service patterns from operator-level signals. A rate alone can be misleading: an extreme percentage may be based on very few calls, while a high-volume operator can contribute more missed calls despite maintaining a comparatively low rate.

The analysis therefore addresses:

- What did inbound service performance look like within calls assigned to operators?
- Which operators contributed most to missed inbound calls?
- How did missed-call rates change when interpreted alongside call volume?
- How did inbound volume, missed calls, and waiting time change over time?
- How did outbound activity vary after accounting for observed active days?

## Dataset and Analytical Scope

The project uses two TripleTen training datasets for the fictional CallMeMaybe virtual-telephony service. The primary dataset contains aggregated call records; `calls_count` represents the number of calls within each record.

The source files are not republished here because their redistribution terms have not been independently confirmed. The notebook documents the required schema, and [`data/README.md`](data/README.md) explains how to supply authorized local copies.

Records without `operator_id` were excluded from operator attribution and analyzed separately because their operational meaning is unresolved. Accordingly, the 0.99% missed rate is specifically the rate among **operator-assigned inbound calls**, not an unrestricted all-call-center rate.

## Analytical Approach

1. Validated source dimensions, schema, missing values, and duplicate records.
2. Removed exact duplicates while preserving unresolved missing categories.
3. Distinguished database records from represented calls.
4. Recalculated waiting time using represented call volume.
5. Developed system-, operator-, and week-level KPI tables.
6. Compared missed-call rate with inbound volume and absolute missed calls.
7. Added Pareto analysis to measure missed-call concentration.
8. Kept outbound volume separate from inbound service-quality signals.

## KPI Framework

| KPI | Calculation | Operational purpose |
|---|---|---|
| Inbound attempts | Sum of `calls_count` for inbound, operator-assigned records | Measure assigned inbound workload |
| Missed inbound calls | Sum of `calls_count` for inbound missed records | Measure absolute missed demand |
| Missed inbound rate | Missed inbound calls / inbound attempts | Compare missed-call incidence with volume context |
| Average inbound wait | Total waiting time / inbound attempts | Measure call-weighted waiting experience |
| Missed-call contribution | Operator missed calls / all assigned-operator missed calls | Identify operational impact |
| Outbound calls per active day | Outbound calls / observed outbound-active days | Describe activity with exposure context |

The optional 10% missed-rate line is a **project analytical reference**, not an SLA, industry benchmark, TripleTen-prescribed threshold, or validated performance standard.

## Key Results

| Result | Operator-assigned population |
|---|---:|
| Inbound attempts | 93,802 |
| Missed inbound calls | 926 |
| Missed inbound rate | 0.99% |
| Average inbound wait per represented call | 13.15 seconds |
| Outbound calls | 608,343 |
| Operators with inbound activity | 754 |
| Operators with outbound activity | 882 |

## Operational Insights

- Rate-based and impact-based prioritization produced different operator views. The 33 operators above the project’s optional 10% reference contributed only 15.12% of assigned-operator missed calls, and their median inbound volume was eight calls.
- Twenty-seven operators accounted for half of assigned-operator missed calls. Reviewing absolute contribution alongside rate provides a more practical investigation starting point.
- Corrected weekly average wait remained within a relatively narrow range across complete weeks even as observed inbound volume and active-operator coverage increased.
- Outbound activity was highly dispersed, but the data does not establish expected outbound responsibilities, scheduled hours, tenure, or assigned workload. It is therefore reported descriptively rather than treated as proof of inefficiency.

## Operator Review Framework

The project does not publish one definitive “inefficient operator” count. Operators are reviewed through multiple signals:

- inbound volume;
- missed inbound calls;
- missed inbound rate;
- share of total missed calls;
- average wait per represented call;
- active inbound days and weekly patterns;
- separate outbound activity context.

An optional 30+ inbound-call view is retained only as an exploratory sensitivity view—not an official eligibility rule.

## Limitations

- Missing operator identifiers cannot be assigned to employees or interpreted operationally without additional source documentation.
- The data does not include scheduled hours, role expectations, routing logic, tenure, call complexity, or assigned workload.
- Project analytical references are not external performance standards.
- Findings identify patterns for further review; they do not prove individual employee inefficiency or causation.
- The current Tableau workbook and Tableau Public dashboard use the original academic calculations and are excluded from the current findings pending a later rebuild.

## Deliverables

- Python notebook with corrected and reproducible KPI logic.
- Operator-level KPI table for review and future dashboarding.
- Weekly system KPI table for trend reporting.
- Pareto/concentration table for missed-call contribution analysis.
- Tableau-ready analytical exports; Tableau rebuild deferred.

## Tools and Methods

**Tools**

- Python: pandas, NumPy, matplotlib, seaborn
- Tableau-ready data preparation

**Methods**

- Data cleaning and validation
- Weighted KPI calculation
- Operational reporting
- Rate-and-volume analysis
- Pareto/concentration analysis
- Time-based reporting

## Repository Structure

```text
call-center-operational-kpi-analysis/
├── README.md
├── Call_Center_Operator_Performance_Analysis.ipynb
├── data/
│   └── README.md
├── outputs/
│   ├── operator_kpis.csv
│   ├── operator_missed_call_pareto.csv
│   └── system_week_kpis.csv
├── docs/
│   ├── tableau-status.md
│   └── academic-history/
│       ├── README.md
│       └── Call_Center_Operator_Performance_Analysis_Academic.ipynb
└── LICENSE
```

Legacy Tableau files remain temporarily in the repository for provenance but are not part of the current analytical deliverables.

## How to Explore

1. Review this README for the business context and findings.
2. Open the [analysis notebook](Call_Center_Operator_Performance_Analysis.ipynb) for the complete calculation logic.
3. Use the three files in [`outputs/`](outputs/) to inspect operator KPIs, weekly reporting, and missed-call concentration.
4. To rerun the analysis, obtain authorized copies of the training datasets and follow [`data/README.md`](data/README.md).

## Project Context

This project originated as a TripleTen Data Analyst training assignment. The original academic work included hypothesis testing and a Tableau dashboard. The current version retains the valid data-quality work, corrects the wait-time calculation, removes unsupported employee-performance classifications, and strengthens the operational reporting design.

---

**Sandra Quinones**  
Business & Operations | Reporting & Data Analysis
