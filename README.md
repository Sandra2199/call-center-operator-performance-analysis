# Call Center Operator Performance Analysis

## Project Overview

This project analyzes call center operator performance using operational KPIs and an interactive Tableau dashboard.

The objective was to identify potentially inefficient operators based on missed call rates, wait times, and call activity metrics. The analysis supports operational decision-making by highlighting performance gaps and opportunities for improvement.

## Business Problem

Call centers rely on timely responses and efficient operator performance to maintain service quality. Management needs a clear way to identify operators who may require additional support, workload adjustments, or performance monitoring.

This project addresses the following questions:

* Which operators show signs of inefficient performance?
* Are missed call rates exceeding acceptable thresholds?
* Do wait times vary significantly across operators?
* Which operators should be prioritized for review?

## Tools Used

* Tableau Public
* Python
* Pandas
* NumPy
* SciPy
* Statistical Hypothesis Testing
* Data Visualization

## Methodology

### Data Preparation

* Cleaned and validated call center operational data.
* Standardized variables and handled missing values.
* Created operator-level performance metrics.

### KPI Development

The following metrics were calculated:

* Inbound Calls
* Outbound Calls
* Missed Inbound Calls
* Missed Call Rate
* Average Wait Time
* Total Calls Handled

### Statistical Analysis

Two hypotheses were tested:

1. Whether the overall missed call rate exceeded the 10% business threshold.
2. Whether wait times differed significantly across operators.

Methods used:

* One-sample z-test for proportions
* Kruskal–Wallis test
* Mann–Whitney U post-hoc comparisons with Holm correction

### Dashboard Design

An interactive Tableau dashboard was developed to monitor:

* Operator efficiency
* Wait time performance
* Missed call rates
* High-risk operators requiring intervention

## Key Findings

* 72 operators (6.6%) were identified as potentially inefficient.
* Average wait time was 57.6 seconds.
* The overall missed call rate remained below the 10% business threshold.
* Significant differences in wait times were observed between operators.
* Several operators exceeded the 180-second wait time threshold.

## Dashboard Preview

<img width="1317" height="992" alt="dashboard_overview" src="https://github.com/user-attachments/assets/291c866c-891a-4116-8d31-672c8c7a9b7a" />

## Interactive Dashboard

Tableau Public Dashboard:

https://public.tableau.com/views/CallCenterOperatorPerformanceAnalysis/CallCenterOperatorPerformanceDashboard

## Project Structure

```text
call-center-operator-performance-analysis/

├── README.md
├── Call_Center_Operator_Performance_Analysis.ipynb
├── Call_Center_Operator_Performance_Analysis.twbx
├── data/
└── images/
```

## Skills Demonstrated

* KPI Development
* Business Analytics
* Operational Performance Monitoring
* Dashboard Design
* Statistical Testing
* Data Visualization
* Tableau Public
* Data Storytelling

## Author

Sandra Quinones

