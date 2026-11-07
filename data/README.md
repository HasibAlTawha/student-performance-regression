# Dataset acquisition and attribution

## Source

- **Dataset:** Student Performance — Mathematics subset, `student-mat.csv`
- **Official source:** https://archive.ics.uci.edu/dataset/320/student+performance
- **Original study:** Cortez, P., & Silva, A. (2008), *Using data mining to predict secondary school student performance*.
- **License:** CC BY 4.0. Retain attribution when reusing or redistributing the dataset.
- **Expected file shape:** 395 student records and 33 columns.
- **Target:** `G3`, final Mathematics grade, on a 0–20 scale.

## How to obtain the data

1. Open the official UCI dataset page linked above.
2. Download the dataset archive and extract `student-mat.csv`.
3. Place the CSV in this `data/` directory so the notebook can read `data/student-mat.csv`. If the notebook uses an automatic download fallback, follow the notebook's own instructions instead.
4. Do not commit the raw CSV unless the project explicitly requires it; this repository documents the source and keeps the raw data out of version control.

The CSV is semicolon-delimited. Preserve the original column names and values so the notebook's feature-selection logic remains reproducible.

## Attribution

Cortez, P., & Silva, A. (2008). *Using data mining to predict secondary school student performance*. Proceedings of the 5th FUBUTEC, 5–12. Dataset record: https://doi.org/10.24432/C5TG7T
