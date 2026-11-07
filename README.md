# Student Performance Prediction Using Regression

A reproducible Statistics project investigating how well selected student characteristics predict final Mathematics grades using regression models.

## Research question

How accurately can final Mathematics grade (`G3`) be predicted from selected demographic, study-habit, family, and attendance-related features when earlier-period grades (`G1` and `G2`) are excluded?

## Project files

- `proposal.md` — initial proposal, with the final scope and unimplemented initial ideas clearly distinguished
- `literature_review.md` — review of five sources related to student-performance prediction
- `methodology.md` — dataset, cleaning, feature engineering, models, evaluation, and limitations
- `experiment.ipynb` — data loading, checks, feature engineering, model fitting, and evaluation
- `requirements.txt` — Python dependencies for running the notebook
- `CONFLICT_NOTES.md` — documentation of the earlier Git merge-conflict exercise
- `data/README.md` — dataset acquisition and attribution instructions

## Dataset

The project uses the Mathematics subset of the UCI Student Performance dataset (395 observations; original file has 33 columns). The target is `G3`, the final grade on a 0–20 scale. The primary experiment excludes `G1` and `G2` because the UCI documentation notes that they are strongly correlated with `G3`.

Source: [UCI Student Performance Dataset](https://archive.ics.uci.edu/dataset/320/student+performance). The dataset is licensed CC BY 4.0; see `data/README.md` for attribution and download instructions. The raw CSV is not committed to this repository.

## Run the experiment

Python 3.10 or newer is recommended.

```bash
python -m venv .venv
# Windows:
.venv\Scripts\activate
# macOS/Linux:
source .venv/bin/activate

python -m pip install --upgrade pip
python -m pip install -r requirements.txt
jupyter lab
```

Open `experiment.ipynb` and use **Restart Kernel and Run All Cells**. The notebook reads `data/student-mat.csv` if present; otherwise it downloads the official UCI ZIP archive, so network access is required on the first run when the CSV is absent. If you download the file manually, place it at `data/student-mat.csv`.

## Models and evaluation

The notebook compares multiple linear regression with Ridge regression using the same deterministic 80/20 holdout split (seed 42). It reports RMSE, MAE, and R-squared on the same test observations. Saved notebook outputs are illustrative until the notebook has been rerun in the environment being used.

## Limitations

Results are exploratory, based on a small observational dataset from two Portuguese schools, and should not be interpreted causally or used for high-stakes decisions. A single holdout split may be variable; cross-validation is a reasonable future extension.
