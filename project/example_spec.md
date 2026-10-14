# Spec: clean_taxis.py

## Goal and user
A cleaned copy of the taxi trips for the team's tip and speed analyses. It will be re-run on each new monthly file.

## Input
`data/taxi_2019.csv` (10,000-row sample). Full monthly files are about 7 million rows with the same columns.

## Output
- `data/taxi_clean.csv`: the kept trips, all original columns, plus `duration_min` and `speed_mph`.
- A printed summary: rows in, rows out, and the number of rows dropped by each rule (a row can break more than one rule).

## Rules
A trip is dropped if any of these apply:
1. Duration under 1 minute or over 3 hours.
2. `trip_distance` is 0 or less, or over 100 miles.
3. `fare_amount` or `total_amount` is 0 or less (refunds and voids).
4. Average speed over 80 mph.
5. `payment_type` is 3 (no charge) or 4 (dispute).

Cash trips (`payment_type` 2) are kept, but their `tip_amount` is set to missing (NaN), because cash tips are not recorded.

## Acceptance criteria
- `test_clean_taxis.py` has a test for each rule and for the cash-tip rule, using small hand-made DataFrames.
- No row in the output breaks any rule.
- Running the script twice gives an identical output file.
- The input file is not modified.

## Performance budget
A 7-million-row month must run in under a minute and 4 GB of memory, so use vectorized pandas only (no `apply` with `axis=1`, no `iterrows`).

## Out of scope
Zone names, and any analysis beyond cleaning.
