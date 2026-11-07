# Student Performance Prediction Using Regression

A reproducible Statistics project investigating how well selected student characteristics predict final Mathematics grades using regression models.

## Refined research question

How accurately can final Mathematics grade (G3) be predicted from selected demographic, study-habit, and attendance-related features when earlier-period grades (G1 and G2) are excluded?

## Project files

- `proposal.md` — initial research proposal and literature scan
- `literature_review.md` — review of five sources related to student-performance prediction
- `methodology.md` — dataset, cleaning, feature engineering, models, and evaluation plan
- `experiment.ipynb` — data cleaning, feature engineering, model fitting, and evaluation with saved output cells
- `CONFLICT_NOTES.md` — documentation of the earlier Git merge-conflict exercise
- `data/README.md` — dataset source and acquisition instructions

## Dataset

The project uses the Mathematics subset of the UCI Student Performance dataset (395 observations; original file has 33 columns). The target is `G3`, the final grade on a 0–20 scale. The primary experiment excludes `G1` and `G2` because the UCI documentation notes that they are strongly correlated with G3.

Source: [UCI Student Performance Dataset](https://archive.ics.uci.edu/dataset/320/student+performance). Cite the dataset and associated study when reusing the data.

## Models and evaluation

The notebook compares multiple linear regression with Ridge regression using a fixed 80/20 holdout split. It reports RMSE, MAE, and R-squared on the same test observations.

## Status

Research design and the first reproducible model-comparison experiment are documented. The results are exploratory, based on a small observational dataset from two Portuguese schools, and should not be interpreted causally or used for high-stakes decisions.
