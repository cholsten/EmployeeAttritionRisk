# Employee Attrition Risk

## Scenario

IBM’s Human Resources team is seeking a model to support strategic efforts to reduce employee attrition. Their goals are to identify key factors linked to higher attrition risk and establish a baseline for average tenure among employees who have left, to help measure the impact of future retention efforts. 

## Overview

Using the [IBM HR Employee Attrition](https://www.kaggle.com/datasets/pavansubhasht/ibm-hr-analytics-attrition-dataset) dataset found on Kaggle (author: Subhasht, P), multiple classification models were compared, with XGBoost emerging as the best fit. SHAP values were applied to interpret feature importance and provide actionable business insights.

## Data & Preparation

Dataset: 1,470 employees, 35 features.

Cleaning: Removed 9 redundant/non-predictive features (e.g., Employee Number, Over 18). No missing values or invalid outliers.

Class Imbalance: Attrition rate ~16%. Addressed via stratified train/test splits, class weights, and threshold adjustments.

Target Metric: Optimized for recall (identifying more at-risk employees).

## Model Performance

| Model | Recall | Precision | F1 |
|---|---|---|---|
| Logistic Regression | 0.34 | 0.67 | 0.45 |
| Random Forest | 0.36 | 0.33 | 0.35 |
| XGBoost | 0.55 | 0.46 | 0.50 |

Confusion Matrix (XGBoost):
Predicted Leave: 26/47 attrition cases correctly identified.
Trade-off: Higher recall means more false positives, but this is acceptable in HR settings where early intervention is preferable.

## Findings/ Insights

Top attrition drivers (via SHAP values):
1. OverTime → Strongest predictor; employees working overtime face higher attrition risk.
2. Stock Option Level → Employees with no stock options are more likely to leave.
3. Age → Employees under 35 show elevated risk.
4. Job Role → Sales roles display higher attrition.
5. Monthly Income → Employees earning <$5,000/month are more likely to leave.

## Potential Action Items

- Monitor and reduce overtime for at-risk employees.
- Expand stock option eligibility to increase retention.
- Enhance engagement programs for younger employees (mentorship, social initiatives).
- Develop targeted retention efforts for the sales team.
- Conduct a compensation review for employees under $5,000/month.
- Establish a tenure goal (i.e. improve from 5.13 years to 7 years).

## Future Analysis

- Explore feature interactions (e.g., Age × Tenure).
- Subgroup analysis (job levels, income bands).
- Address class imbalance with synthetic oversampling (SMOTE).
- Investigate time-based attrition patterns.
