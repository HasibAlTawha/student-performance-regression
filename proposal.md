# Project Proposal

> **Scope note:** This document records the initial proposal. After reviewing the dataset and narrowing the research question, the implemented experiment was refined as documented in `methodology.md`. The final experiment—not every exploratory idea below—is the basis for the reported results.

## 1. Research question

How accurately can final Mathematics grade (`G3`) be predicted from selected demographic, study-habit, family, and attendance-related features when earlier-period grades (`G1` and `G2`) are excluded?

The project compares multiple linear regression and Ridge regression on the same held-out observations. It is a predictive, exploratory analysis; coefficients are not interpreted as causal effects.

## 2. Dataset

- **Name:** UCI Student Performance — Mathematics subset (`student-mat.csv`)
- **Source:** [UCI Machine Learning Repository](https://archive.ics.uci.edu/dataset/320/student+performance)
- **Original study:** Cortez and Silva (2008)
- **License:** CC BY 4.0; attribute the source when reusing the data
- **Size:** 395 observations and 33 original columns
- **Target:** `G3`, final Mathematics grade on a 0–20 scale
- **Primary predictors:** `age`, `studytime`, `absences`, `famrel`, `freetime`, `goout`, and `health`
- **Engineered predictors:** `prior_failure_flag` (whether `failures > 0`) and `studytime_high` (whether `studytime >= 3`)

The final model excludes `G1` and `G2` because they are strongly correlated with `G3` and would change the research question to one that relies on earlier grades. The raw `failures` field is used to construct the binary indicator and is not also included in the predictor matrix.

## 3. Related work and motivation

1. **Cortez and Silva (2008)** introduced the dataset and studied data-mining approaches to student performance. Their work highlights the predictive value of earlier-period grades.
2. **Yağcı (2022)** studied machine-learning approaches to predicting academic performance in a different educational setting. Its findings provide context for comparing prediction methods, but its reported results are not directly comparable to this dataset or regression task.

This project uses a transparent regression baseline and a regularized alternative, with a deliberate focus on non-grade features. The scope is narrower than the initial idea of comparing models with and without `G1`/`G2`, and the implemented notebook does not claim coefficient significance tests or a full diagnostic analysis.

## 4. Implemented method

1. Obtain the official Mathematics CSV and inspect its dimensions and required columns.
2. Check missing values and construct the two documented binary features.
3. Use a deterministic 80/20 train/test split (random seed 42).
4. Fit multiple linear regression and Ridge regression; standardize features within the Ridge pipeline.
5. Evaluate both models on the same test set using RMSE, MAE, and R-squared.

The current notebook reports predictive metrics. Adjusted R-squared, coefficient significance tests, VIF, and formal residual diagnostics were ideas from the initial plan, not completed analyses; they should not be described as project results unless implemented in a future revision.

## 5. Expected contribution and limitations

The project demonstrates a reproducible regression workflow and evaluates how informative a small set of non-grade student characteristics is for predicting `G3`. Results are exploratory: the data are observational, contain 395 students from two Portuguese schools, and may not generalize to other populations. Prediction metrics do not establish causality, fairness, or suitability for high-stakes student decisions.

## References

- Cortez, P., & Silva, A. (2008). *Using data mining to predict secondary school student performance*. Proceedings of the 5th FUBUTEC, 5–12.
- Yağcı, M. (2022). Educational data mining: prediction of students' academic performance using machine learning algorithms. *Smart Learning Environments, 9*, Article 11. https://doi.org/10.1186/s40561-022-00192-z
- UCI Machine Learning Repository. *Student Performance*. https://doi.org/10.24432/C5TG7T
