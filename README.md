Two-Stage Hybrid XAI Framework for Equitable Diabetes Prediction

Project Overview
This project proposes a two-stage hybrid explainable AI framework for equitable diabetes prediction, specifically focused on improving explanation quality for minority class (diabetic) patients. The framework combines SHAP-anchored LIME for stable local explanations with DiCE counterfactuals for actionable clinical recourse.   

Datasets
PIMA Indian Diabetes Dataset: 
Sourced from the UCI Machine Learning Repository, containing 768 samples and 8 continuous clinical features with a 1.87:1 class imbalance ratio. Zero values in features like Insulin and BMI were replaced with the column median.   
CDC Diabetes Health Indicators Dataset: 
Sourced from the UCI Machine Learning Repository, containing 253,680 records and 21 mixed features (binary and continuous) with a 6.18:1 class imbalance ratio.   

Methodology
Preprocessing: 
Applied an 80/20 stratified train-test split alongside a StandardScaler. SMOTE was applied exclusively to the training data inside cross-validation folds to prevent data leakage.   
Modeling: 
XGBoost was selected as the primary model over Neural Networks due to higher recall, which minimizes missed diabetic diagnoses in a clinical screening context.   
Explainability (XAI): 
Implemented SHAP for global feature importance, a custom SHAP-anchored LIME pipeline to prevent explanation drift, and DiCE for clinical counterfactuals.   

Key Findings
Imbalance Degrades Performance: 
Higher class imbalance directly degrades minority class prediction quality even after applying SMOTE.   
SHAP Quality Drops for Minority Class: 
The model relies on key predictors less confidently when explaining minority class predictions; for instance, BMI drops 31% in SHAP magnitude on the PIMA dataset.   
LIME Drift is Proportional to Imbalance: 
Standard LIME explanation drift increases with severe class imbalance; SHAP-anchoring eliminated this drift on PIMA (96% consistency) and substantially reduced it on CDC.   
DiCE Actionability Depends on Dataset: 
Counterfactuals were clinically actionable on continuous biomarkers (PIMA) but predominantly non-actionable (89%) on binary survey features (CDC).   
Algorithmic Bias: 
The model systematically missed younger patients on the PIMA dataset because their clinical values fell below the model's detection thresholds, which appear calibrated for older, more severely symptomatic patients. 
