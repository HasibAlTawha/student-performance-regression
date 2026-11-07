# Methodology: Student Performance Prediction Using Regression

## 1. Refined research question

Among students in the Mathematics subset of the UCI Student Performance dataset, how accurately can final Mathematics grade (G3) be predicted from selected demographic, study-habit, family, and attendance-related variables when earlier-period grades (G1 and G2) are excluded?

The analysis is predictive and exploratory. It will not interpret feature associations as causal effects or as evidence that a student should receive a consequential intervention.

## 2. Dataset description

- **Dataset:** Student Performance — Mathematics subset, `student-mat.csv`.
- **Source:** UCI Machine Learning Repository: https://archive.ics.uci.edu/dataset/320/student+performance
- **Original study:** Cortez and Silva (2008).
- **License:** CC BY 4.0, with attribution.
- **Expected size:** 395 student records and 33 columns in the original Mathematics CSV.
- **Target:** `G3`, the final Mathematics grade on a 0–20 scale.
- **Primary candidate features:** `age`, `studytime`, `absences`, `famrel`, `freetime`, `goout`, and `health`.
- **Engineered features:** `prior_failure_flag` (1 if `failures > 0`, otherwise 0) and `studytime_high` (1 if the reported study-time category is 3 or 4, otherwise 0). The raw `failures` variable is used to construct the indicator and is then excluded from the model matrix to avoid redundant predictors.

The primary model intentionally excludes `G1` and `G2`. UCI notes that these earlier grades are strongly correlated with G3; including them may inflate apparent predictive performance and is less aligned with a question about prediction from non-grade characteristics.

## 3. Data cleaning plan

1. Load the semicolon-delimited CSV and inspect dimensions, column names, data types, and sample rows.
2. Check duplicate records and missing values; report the checks before deciding whether rows need to be removed or imputed.
3. Convert candidate features and the target to numeric values, coercing invalid values to missing and checking them explicitly.
4. Confirm that `G3` falls within its documented 0–20 range and inspect distributions for unusual values.
5. Use a fixed random seed for the train/test split so the experiment is reproducible.
6. Fit all learned preprocessing only on the training data to avoid leakage. The selected primary features are numeric, so no categorical encoding is required for the initial model.

## 4. Feature engineering

The two binary indicators described above provide a simple alternative representation of prior failure and higher reported study-time category. They are added alongside the original numeric predictors. The raw `failures` variable is used for feature construction but excluded from the final predictor matrix. `G1` and `G2` will be excluded from the primary model; a later sensitivity analysis could include them, but it must be clearly labelled as a different prediction scenario.

## 5. Models and rationale

### Model A — Multiple Linear Regression

Linear regression is an interpretable baseline that estimates the relationship between the selected predictors and G3. It is suitable for a Statistics project because coefficients and residuals can be inspected, while its assumptions and limitations can be discussed directly.

### Model B — Ridge Regression

Ridge regression adds an L2 penalty to the linear model's coefficients. It is a useful comparison because correlated predictors can make ordinary least-squares coefficients unstable; regularization can reduce coefficient variance. Numeric features will be standardized within a pipeline for Ridge, with scaling fitted only on the training data.

Both models will use the same train/test split and the same primary predictors. The models are not assumed to capture all nonlinear relationships.

## 6. Evaluation metrics

- **Root Mean Squared Error (RMSE):** reports prediction error in grade points and penalizes larger errors more heavily. Lower is better.
- **Mean Absolute Error (MAE):** reports the average absolute prediction error in grade points and is less sensitive to a few large errors than RMSE. Lower is better.
- **R-squared (R²):** describes how much test-set variation is explained relative to predicting the test-set mean. Higher is generally better, but it can be negative on test data.

A fixed 80/20 holdout split with a documented random seed will be used for the primary comparison. With only 395 observations, results can vary by split; cross-validation would be a sensible follow-up. Metrics alone do not establish causality or fairness.

## 7. Reproducibility and limitations

The notebook will report the dataset shape, cleaning checks, feature list, split configuration, and model metrics. The raw dataset should be obtained from the official UCI page and kept out of Git if repository rules exclude raw CSV files; the notebook can download and extract it when a local copy is absent.

The dataset comes from two schools in Portugal and may not generalize to Bangladesh or other education systems. It is observational, relatively small, and contains self-reported measures. The target is a school grade rather than a direct measure of learning, and performance metrics do not justify high-stakes use for individual students.
