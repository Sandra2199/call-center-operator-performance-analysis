# Source Data Instructions

The original CallMeMaybe datasets are not republished in this repository because their redistribution terms have not been independently confirmed.

To reproduce the analysis, obtain authorized copies from the original TripleTen project materials and place them in this directory using these filenames:

```text
data/
├── telecom_dataset_us.csv
└── telecom_clients_us.csv
```

## Required call dataset schema

`telecom_dataset_us.csv` must contain:

| Field | Definition |
|---|---|
| `user_id` | Client account ID |
| `date` | Date when statistics were retrieved |
| `direction` | Call direction: `in` or `out` |
| `internal` | Whether the call was internal |
| `operator_id` | Operator identifier |
| `is_missed_call` | Whether the represented call group was missed |
| `calls_count` | Number of represented calls |
| `call_duration` | Call duration excluding waiting time |
| `total_call_duration` | Call duration including waiting time |

Verified source fingerprint:

- 53,902 rows;
- 9 columns;
- 4,900 exact duplicate rows before cleaning.

## Required client dataset schema

`telecom_clients_us.csv` must contain:

- `user_id`
- `tariff_plan`
- `date_start`

The client file is retained for source completeness but is not required for the core operator KPI calculations.

Do not substitute a similarly named file without validating its schema and source fingerprint.

