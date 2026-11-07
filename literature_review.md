# Literature Review: Student Performance Prediction

This review focuses on student-grade prediction, the selected public dataset, and evaluation practices for educational prediction models.

## 1. Cortez and Silva (2008) — Using Data Mining to Predict Secondary School Student Performance

Cortez and Silva investigate how data-mining methods can predict secondary-school achievement using demographic, social, school, and prior-grade variables. Their work introduced the student performance data now hosted by the UCI Machine Learning Repository and provides the direct foundation for this project. The present analysis narrows the question to Mathematics final grade and deliberately excludes G1 and G2 from the primary feature set to avoid relying on earlier grades that are strongly associated with G3.

**Source:** Cortez, P., & Silva, A. M. G. (2008). *Using data mining to predict secondary school student performance*. Proceedings of the 5th Annual Future Business Technology Conference. Dataset and paper details: https://archive.ics.uci.edu/dataset/320/student+performance

## 2. Zhang et al. (2021) — Educational Data Mining Techniques for Student Performance Prediction: Method Review and Comparison Analysis

Zhang and colleagues review student-performance prediction across data collection, problem formulation, model selection, prediction, and application. They also compare traditional machine-learning methods on educational datasets and discuss evaluation approaches such as RMSE for regression. This supports a transparent, reproducible comparison of more than one model using a consistent train/test split rather than reporting a single model in isolation.

**Source:** Zhang, Y., Yun, Y., An, R., Cui, J., Dai, H., & Shang, X. (2021). *Educational Data Mining Techniques for Student Performance Prediction: Method Review and Comparison Analysis*. Frontiers in Psychology, 12, 698490. https://doi.org/10.3389/fpsyg.2021.698490

## 3. UCI Machine Learning Repository — Student Performance Dataset

The UCI dataset documentation describes two Portuguese secondary-school course datasets and the associated demographic, social, school, and grade variables. It notes that G1 and G2 are strongly correlated with G3, which is an important design consideration because including them can make grade prediction easier while reducing the practical value of the model for earlier intervention. The documentation also provides the dataset citation and licensing information, which informs reproducibility and attribution.

**Source:** Cortez, P. (2008). *Student Performance* [Dataset]. UCI Machine Learning Repository. https://doi.org/10.24432/C5TG7T

## 4. Chicco, Warrens, and Jurman (2021) — The coefficient of determination R-squared is more informative than SMAPE, MAE, MAPE, MSE and RMSE in regression analysis evaluation

This article discusses the strengths and limitations of common regression evaluation metrics and argues that R-squared can provide useful complementary information about a model's explanatory performance. For this project, R-squared will be reported alongside RMSE and MAE rather than used alone: RMSE emphasizes larger errors, MAE is easier to interpret as an average absolute grade error, and R-squared summarizes the proportion of test-set variation explained relative to a mean baseline.

**Source:** Chicco, D., Warrens, M. J., & Jurman, G. (2021). *The coefficient of determination R-squared is more informative than SMAPE, MAE, MAPE, MSE and RMSE in regression analysis evaluation*. PeerJ Computer Science, 7, e623. https://doi.org/10.7717/peerj-cs.623

## 5. Scikit-learn documentation — Model evaluation and regression metrics

The scikit-learn documentation defines regression metrics such as mean absolute error, mean squared error, and R-squared, and explains how these functions can be applied consistently to predictions from different estimators. Using a standard library implementation reduces the chance of inconsistent metric calculations between models. The project will use the same held-out observations for both models and report the metrics in a single comparison table.

**Source:** scikit-learn developers. *Model evaluation: quantifying the quality of predictions*. https://scikit-learn.org/stable/modules/model_evaluation.html

## Synthesis and research gap

The sources establish that student achievement prediction is a recognized educational data-mining task, that the UCI dataset is suitable for a reproducible baseline study, and that model evaluation should use clearly defined metrics. This small project will not claim to establish causal effects or produce a deployable student-risk system. Instead, it will compare an interpretable linear model with a regularized linear model using selected pre-final-grade characteristics, and discuss the limitations of the small, geographically specific observational dataset.
