# House Prices Prediction – Ames Housing Dataset

---

## Overview

This project demonstrates a **complete regression workflow** for predicting house prices using the **Ames Housing Dataset** (Kaggle: *House Prices - Advanced Regression Techniques*).

It includes:

* **Exploratory Data Analysis (EDA)** to understand feature distributions, correlations, outliers, and missing values.
* **Preprocessing pipelines** for numerical and categorical features.
* **Model training** using linear, regularized, and tree-based algorithms.
* **Hyperparameter tuning** and evaluation.
* **Exported models** ready for prediction.

---

## Directory Structure

```
housePricesModel/
│
├── EDA.ipynb                     # Initial EDA (basic stats, missing values, visuals)
├── EDA2.ipynb                    # Extended EDA (univariate, bivariate, outliers, correlations)
├── model.ipynb                   # Full modeling pipeline: preprocessing, training, tuning, evaluation, export
├── train.csv                     # Training data (1460 rows × 81 columns)
├── test.csv                      # Test data (1459 rows × 80 columns)
│
└── fine_tuned_models/            # Saved model pipelines
    ├── GradientBoosting_model_pipeline.pkl
    ├── Lasso_model_pipeline.pkl
    ├── LinearRegression_model_pipeline.pkl
    └── (Ridge & RandomForest saved in notebook)
```

---

## Dataset

* **Source**: [Kaggle - House Prices](https://www.kaggle.com/c/house-prices-advanced-regression-techniques)
* **Training Set**: 1460 samples × 80 features + target (`SalePrice`)
* **Test Set**: 1459 samples × 80 features (target withheld)
* **Feature Types**: 38 numerical, 43 categorical (including ordinal)

> **Target**: `SalePrice` — right-skewed (log-transformed to reduce skewness for linear models).

---

## Key EDA Findings

| Insight                 | Details                                                                             |
| ----------------------- | ----------------------------------------------------------------------------------- |
| **Missing Values**      | `PoolQC` (99.7%), `MiscFeature` (96%), `Alley` (93%), `Fence` (80%)                 |
| **Outliers**            | Extreme values in `GrLivArea`, `LotArea`; 61 outliers detected in `SalePrice`       |
| **Strong Correlations** | `OverallQual` (0.79), `GrLivArea` (0.71), `GarageCars` (0.64), `TotalBsmtSF` (0.61) |
| **Categorical Drivers** | `Neighborhood`, `ExterQual`, `KitchenQual`, `GarageFinish`                          |
| **Skewed Features**     | `SalePrice`, `LotArea`, `GrLivArea` → log-transform applied                         |

> Visuals include histograms, boxplots, scatter plots, and heatmaps.

---

## Preprocessing Pipeline

* **Numerical Features**: `SimpleImputer(median)` → `StandardScaler`
* **Categorical Features**: `SimpleImputer(most_frequent)` → `OneHotEncoder(handle_unknown='ignore')`
* **Outlier Handling**:

  * Skewed features (>1): IQR × 3
  * Normal-like: Z-score > 3
  * Applied only on training data

---

## Models Trained

| Model            | Type   | Base CV R² | Tuned CV R² |
| ---------------- | ------ | ---------- | ----------- |
| LinearRegression | Linear | 0.912      | —           |
| Ridge            | Linear | 0.907      | 0.860       |
| Lasso            | Linear | -0.006     | 0.861       |
| RandomForest     | Tree   | 0.885      | 0.861       |
| GradientBoosting | Tree   | 0.898      | 0.887       |

> **Winner (CV Generalization)**: Gradient Boosting
> **Best Test Score**: Linear Regression (R² = 0.912)

---

## Hyperparameter Tuning (RandomizedSearchCV)

| Model            | Best Parameters                                        |
| ---------------- | ------------------------------------------------------ |
| GradientBoosting | `n_estimators=300`, `max_depth=3`, `learning_rate=0.1` |
| Lasso            | `alpha=0.001`, `max_iter=1000`                         |
| Ridge            | `alpha=46.4`, `solver='lsqr'`                          |
| RandomForest     | `n_estimators=300`, `max_depth=30`                     |

---

## Model Evaluation (Test Set)

| Model            | RMSE  | R²     |
| ---------------- | ----- | ------ |
| LinearRegression | 0.128 | 0.912  |
| Ridge            | 0.132 | 0.907  |
| GradientBoosting | 0.138 | 0.898  |
| RandomForest     | 0.147 | 0.885  |
| Lasso            | 0.433 | -0.006 |

---

## Model Interpretation

* **Linear Models**:
  Positive: `OverallQual`, `GrLivArea`, `Neighborhood_Crawfor`
  Negative: `MSZoning_RM`, `CentralAir_N`

* **Tree Models** (Feature Importance):

| Rank | Feature            | Importance |
| ---- | ------------------ | ---------- |
| 1    | `OverallQual`      | 0.432      |
| 2    | `GrLivArea`        | 0.175      |
| 3    | `TotalBsmtSF`      | 0.045      |
| 4    | `GarageFinish_Unf` | 0.042      |
| 5    | `GarageCars`       | 0.038      |

---

## Saved Models (`fine_tuned_models/`)

| File                                  | Model             | Notes                              |
| ------------------------------------- | ----------------- | ---------------------------------- |
| `GradientBoosting_model_pipeline.pkl` | Gradient Boosting | Best CV generalization             |
| `Lasso_model_pipeline.pkl`            | Lasso             | Sparse linear model, interpretable |
| `LinearRegression_model_pipeline.pkl` | Linear Regression | Best test R², simple baseline      |

> Ridge and RandomForest saved in notebook but not exported to directory.

---

## Usage Example

```python
import joblib
import pandas as pd
import numpy as np

# Load model
model = joblib.load('fine_tuned_models/GradientBoosting_model_pipeline.pkl')

# Load test set
test = pd.read_csv('test.csv')

# Predict
predictions = model.predict(test)

# Reverse log-transform
saleprice_pred = np.expm1(predictions)

# Save submission
submission = pd.DataFrame({'Id': test.Id, 'SalePrice': saleprice_pred})
submission.to_csv('submission.csv', index=False)
```

---

## Recommendations

| Goal                | Model             |
| ------------------- | ----------------- |
| Best Generalization | Gradient Boosting |
| Best Test Score     | Linear Regression |
| Interpretability    | Lasso             |
| Kaggle Submission   | Gradient Boosting |

> Consider stacking Linear + Gradient Boosting for further performance improvement.

---
