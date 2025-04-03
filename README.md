## Project Description

This project presents a complete machine learning pipeline for classifying **users vs bots** on a social media platform using behavioral and profile-based features. The goal is to build an interpretable, high-performing model that can reliably distinguish between real users and automated bots to support platform integrity and moderation efforts.

---

## Business Impact

- Detects bots with high precision, helping reduce fake activity  
- Improves trust and safety by identifying suspicious profiles early  
- Lightweight model enables fast deployment without sacrificing interpretability  
- SHAP provides clear justifications for predictions — essential for stakeholder trust and audits

---

## Workflow Overview

1. **Data Cleaning & Preprocessing**  
   - Converted object columns to numeric  
   - Replaced missing values with standardized placeholders (`-999`)  
   - Dropped high-cardinality feature `city`

2. **Train/Validation/Test Split**  
   - Stratified split: 60% train, 20% validation, 20% test

3. **Model Training**  
   - XGBoost classifier tuned using **Optuna**  
   - Evaluation metric: `logloss`  
   - Early stopping applied to avoid overfitting

4. **Explainability with SHAP**  
   - Used SHAP values to interpret model predictions  
   - Identified top 17 features contributing most to classification

5. **Feature Reduction**  
   - Reduced original 59 predictors to 17 based on SHAP importance  
   - Maintained performance while improving simplicity and interpretability

6. **Model Evaluation**  
   - Measured performance across all splits using `classification_report`  
   - Visualized predictions and SHAP beeswarm plots

---

## Technical Results

| Dataset    | F1 Score | Accuracy |
|------------|----------|----------|
| Train      | 0.98     | 0.98     |
| Validation | 0.98     | 0.98     |
| Test       | 0.97     | 0.97     |

- Balanced performance across both bot and user classes  
- Minimal performance drop after feature reduction  
- SHAP confirms strong feature separability and model trustworthiness

---

Kaggle Notebook:
https://www.kaggle.com/code/kennethr/distinguishing-bots-from-users-val-f1-98
