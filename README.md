🧠 Healthcare Cost Prediction (SOFTEC’26 ML Competition)
📌 Overview

This project focuses on predicting whether a healthcare member will incur high medical costs (> $30,000) in the next year. The task is a binary classification problem using structured healthcare data.

🎯 Objective

Predict HighCostLabel:

1 → High cost (> $30,000)
0 → Low cost (≤ $30,000)
📊 Dataset

The data consists of multiple tables:

main_df → Member-level aggregated features
cpt_df → Procedure records
icd_df → Diagnosis records
drg_df → Claim groupings
dob_df → Demographics
⚙️ Approach
🔹 Data Processing
Filtered rows using MONTH = -1, 12 (valid prediction points)
Removed leakage feature: NEXT_YEAR_COST
Merged demographic data via Member_Key
🔹 Feature Engineering
Aggregated CPT, ICD, DRG tables:
Count features
Unique counts
Handled missing values:
Numerical → 0
Consistent preprocessing for train/test
🔹 Validation Strategy
Used time-based split:
Train → 2021–2022
Validation → 2023
Avoided random K-Fold to prevent temporal leakage
🔹 Model
LightGBM Classifier
Handled imbalance using class_weight='balanced'
🔹 Optimization
Tuned classification threshold to maximize F1 score
📈 Evaluation Metrics
F1 Score (Primary)
Precision
Recall
ROC-AUC
PR-AUC
📂 Files
model.py / notebook → Training pipeline
submission.csv → Predictions
🚀 Key Learnings
Time-based validation is critical for realistic performance
Feature aggregation significantly improves results
Avoiding leakage is more important than complex models
🔮 Future Improvements
Time-series features (trends, lag features)
Advanced models (CatBoost, ensembles)
Better categorical encoding


