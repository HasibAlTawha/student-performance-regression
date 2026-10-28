# Project Proposal

## 1. Research Question
Which demographic, behavioral, and school-related factors most strongly predict
the final grade (G3) of secondary-school mathematics students, and how accurately
can a multiple linear regression model predict it?

## 2. Dataset
- **Name:** Student Performance Data Set
- **Source:** UCI Machine Learning Repository (Cortez & Silva, 2008)
- **Link:** https://archive.ics.uci.edu/dataset/320/student+performance
- **License:** CC BY 4.0
- **Size:** 395 records (mathematics course), 33 attributes
- **Target variable:** G3 (final grade, 0 to 20)
- **Predictors:** age, study time, failures, absences, parental education,
  alcohol consumption, internet access, G1 and G2 (period grades), among others

## 3. Existing Work (Two-Source Scan)
1. **Cortez & Silva (2008)** built the dataset and compared decision trees,
   random forests, neural networks, and SVMs for predicting student grades.
   *Finding:* models using the earlier period grades (G1, G2) predicted G3 far
   better than models using only demographic and social features.
   *Gap:* it does not interpret individual predictor effects, which a
   regression model can.
2. **Yağcı (2022)** predicted undergraduate students' final exam outcomes
   from their midterm grades, comparing random forest, SVM, logistic
   regression, Naïve Bayes, and k-NN classifiers.
   *Method:* supervised classification (pass/fail style outcomes).
   *Finding:* reported classification accuracy of about 70-75%, showing that
   earlier grades carry most of the predictive signal.
   *Gap:* it treats the outcome as a category, uses university data, and
   focuses on accuracy rather than the size of each factor's effect. This
   project models a continuous grade (G3) in secondary school and estimates
   each predictor's effect.

**Synthesis:** Existing work emphasizes predictive accuracy using
black-box models. This project instead uses interpretable linear regression
to quantify each factor's effect and test whether non-grade factors add
explanatory power once G1 and G2 are controlled.

## 4. Planned Method
1. Exploratory data analysis (distributions, correlations, missing values)
2. Preprocessing (encode categorical variables, check outliers)
3. Fit two models: with G1/G2 and without G1/G2
4. Evaluate: R², adjusted R², RMSE on a train/test split
5. Diagnostics: residual plots, VIF for multicollinearity, normality of residuals

## 5. Expected Outcome
A ranked set of significant predictors of G3 and a comparison of model
performance with and without prior grades.

## References
- Cortez, P., & Silva, A. (2008). Using data mining to predict secondary school
  student performance. In *Proc. 5th FUBUTEC*, pp. 5-12.
- Yağcı, M. (2022). Educational data mining: prediction of students' academic
  performance using machine learning algorithms. *Smart Learning Environments*,
  9(11). https://doi.org/10.1186/s40561-022-00192-z