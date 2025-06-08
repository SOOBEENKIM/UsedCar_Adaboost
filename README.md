# 🚗 Used Car Price Prediction with Tree-Based Models

This project aims to predict used car transaction prices using structured car dataset features and machine learning models such as Decision Tree, Random Forest, and AdaBoost. The work was carried out as part of an applied data analytics course project, with a focus on feature engineering, dimensionality reduction, and model performance evaluation.

---

## 📂 Project Overview

- **Goal**: Predict the `SUCCESSPRICE` (final transaction price) of used vehicles based on car features and domain-informed transformations.
- **Dataset**: Structured tabular data from a certified car price authority, with features including manufacturing year, engine type, usage type, distance, shipping cost, etc.
- **Key Approach**:
  - Extensive feature engineering using both domain knowledge and PCA
  - Tree-based ensemble models with hyperparameter tuning via grid search
  - Custom test sets and visualization-based interpretation

---

## 🛠️ Feature Engineering Highlights

- Missing value treatment:
  - Median imputation for continuous variables
  - Custom category imputation for discrete variables
- Encoding:
  - Label Encoding (e.g., `USEUSENM`, `FUELNM`)
  - Ordinal Encoding (e.g., `COLOR`, `MISSNM`, `GRADE_KEY`)
  - One-Hot Encoding (binary flags)
- Derived Features:
  - Vehicle age
  - Model-wise average `SUCCESSPRICE`
  - Price binning based on model grade (partial implementation)
- Dimensionality Reduction:
  - PCA reduced 5 continuous variables to 4 principal components

---

## 🤖 Models & Evaluation

- **Models Used**:
  - Decision Tree
  - Random Forest
  - AdaBoost

- **Metrics**:
  - MAE, MSE, Adjusted R², Error Rate

- **Best Result** (Custom Test Set):
  | Model       | MAE      | MSE             | R² (Adj.) | Error Rate |
  |-------------|----------|------------------|------------|-------------|
  | DecisionTree| 850,623  | 1.66e+12         | 0.9612     | 12.80%      |
  | RandomForest| 579,384  | 7.63e+11         | 0.9822     | 9.07%       |
  | AdaBoost    | 569,462  | 7.37e+11         | 0.9828     | **8.70%**   |

→ **AdaBoost** achieved the best overall performance with lowest error.

---

## 🧠 Feedback & Future Improvement

This section summarizes feedback received post-presentation and outlines future enhancements.

### 🔧 Modeling Improvements
- **Randomness Sensitivity**: `random_state` and `max_depth` affected results significantly. Optimal hyperparameter intervals were found via repeated trials.
- **Train-Test Sampling**: Visual differences in train/test distribution suggest potential overfitting or sampling bias.

### 📉 Feature Improvements
- **PCA**: Dimensionality reduction worked, but better interpretation needed on multicollinearity between continuous features.
- **Winsorization**: Should be applied to target values with extreme variance (e.g., when used car prices drop sharply).
- **Model-Wise Aggregation**: Mean `SUCCESSPRICE` by `GRADE_KEY` was partially implemented — binning strategy needs full integration.

### ⚠️ Data Quality Concerns
- Non-standard value distributions across models affected residuals.
- Use of `average success price` to replace missing values needs revalidation — especially when market-specific pricing bias exists.

---

## ✅ Next Steps

- Apply feature correlation analysis before dimensionality reduction
- Revisit PCA assumptions (stationarity, scale variance)
- Implement validation strategy using cross-validation
- Address outliers using both winsorization and rule-based exclusions
- Standardize success price aggregation method per model

---
