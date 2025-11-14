# Medical Insurance Forecasting

---

## Overview

This project investigates the factors influencing medical insurance charges and develops predictive models to estimate costs based on demographic and health-related variables. Using exploratory data analysis (EDA), statistical testing, and machine learning techniques, this study identifies key predictors of insurance charges and builds regression models to forecast future costs.

---

## Objectives

* Analyze the distribution and relationships of features affecting medical insurance charges.
* Perform statistical tests to identify significant differences in charges across groups.
* Preprocess data to handle skewness, outliers, and categorical encoding.
* Develop and evaluate multiple regression models for predictive accuracy.
* Optimize model performance through hyperparameter tuning.

---

## Dataset

The dataset comprises 1,338 records with the following variables:

| Feature  | Type        | Description                         |
| -------- | ----------- | ----------------------------------- |
| age      | Numeric     | Age of the policyholder             |
| sex      | Categorical | Gender of the policyholder          |
| bmi      | Numeric     | Body Mass Index (BMI)               |
| children | Numeric     | Number of dependents                |
| smoker   | Categorical | Smoking status (yes/no)             |
| region   | Categorical | Residential region in the US        |
| charges  | Numeric     | Insurance charges (target variable) |

**Source:** [Kaggle - Medical Insurance Dataset](https://www.kaggle.com/datasets/mirichoi0218/insurance)

---

## Methodology

### 1. Exploratory Data Analysis (EDA)

Performed in `EDA.ipynb`, EDA includes:

* Summary statistics and missing value analysis
* Visualization of distributions (histograms, boxplots, scatter plots)
* Correlation analysis between numeric variables
* Target mean plots across categorical features
* Statistical tests:

  * Independent T-test for binary categories (sex, smoker)
  * One-way ANOVA for multi-class categories (region)

**Key Insights:**

| Feature  | Observation                                                                       |
| -------- | --------------------------------------------------------------------------------- |
| Age      | Moderate positive correlation with charges; older individuals tend to pay more.   |
| BMI      | Slight positive correlation; overweight or obese individuals have higher charges. |
| Children | Minimal effect on charges; number of dependents not a major predictor.            |
| Smoker   | Significant impact; smokers incur much higher charges.                            |
| Sex      | Slight difference; males tend to have marginally higher charges.                  |
| Region   | Insignificant effect on charges after accounting for other features.              |
| Charges  | Right-skewed distribution; outliers correspond to extreme health cases.           |

---

### 2. Data Preprocessing

Performed in `Medical Insurance Forecast Model.ipynb`:

* **Train/Validation/Test Split:** Ensured stratification to preserve target distribution
* **Outlier Treatment:** Using Z-score and IQR methods for numeric features
* **Feature Engineering:** Skewed features scaled using RobustScaler; normal features with StandardScaler
* **Encoding:** One-hot encoding for categorical features

---

### 3. Modeling

Multiple regression models were trained and evaluated using RMSE and R²:

| Model             | Validation RMSE | Validation R² |
| ----------------- | --------------- | ------------- |
| Random Forest     | 5,221.23        | 0.805         |
| Gradient Boosting | 5,369.52        | 0.794         |
| Ridge Regression  | 8,919.83        | 0.431         |
| Linear Regression | 8,972.43        | 0.424         |
| Huber Regression  | 9,696.30        | 0.327         |
| Lasso Regression  | 12,573.69       | -0.131        |

Random Forest and Gradient Boosting models performed the best in predicting insurance charges.

---

### 4. Feature Importance

For ensemble models (Random Forest & Gradient Boosting), feature importance was computed:

| Feature  | Importance Score (RF) | Importance Score (GB) | Interpretation                                                      |
| -------- | --------------------- | --------------------- | ------------------------------------------------------------------- |
| Smoker   | 0.63                  | 0.58                  | Most influential; smoking drastically increases charges             |
| Age      | 0.20                  | 0.25                  | Older individuals tend to incur higher costs                        |
| BMI      | 0.12                  | 0.14                  | Health-related predictor; higher BMI correlates with higher charges |
| Children | 0.03                  | 0.02                  | Minor effect on charges                                             |
| Region   | 0.01                  | 0.01                  | Minimal impact                                                      |
| Sex      | 0.01                  | 0.00                  | Negligible effect                                                   |

**Insight:** Smoking, age, and BMI are the primary determinants of insurance costs.

---

### 5. Hyperparameter Tuning

Hyperparameters for the top-performing models were optimized using `RandomizedSearchCV` to improve predictive accuracy. Tuned models achieved slightly better RMSE and R² scores, confirming the robustness of ensemble methods for this task.

---

### 6. Evaluation

* Residual plots and actual vs predicted scatter plots were used to assess model performance.
* Learning curves were analyzed to detect underfitting or overfitting.
* Random Forest and Gradient Boosting demonstrated low bias and acceptable variance.

---

## Tools & Technologies

* **Programming Language:** Python 3.x
* **Libraries:** Pandas, NumPy, Matplotlib, Seaborn, Scikit-learn, SciPy, Statsmodels
* **Development Environment:** Jupyter Notebook

---

## Project Structure

```
Medical Insurance Forecast/
│
├── EDA.ipynb                           # Exploratory Data Analysis
├── Medical Insurance Forecast Model.ipynb  # Data preprocessing, modeling, tuning
└── README.md                           # Project documentation
```

---

## How to Run

1. Clone the repository:

```bash
git clone <repository-url>
```

2. Install dependencies:

```bash
pip install -r requirements.txt
```

3. Open notebooks in Jupyter and run sequentially:

   * `EDA.ipynb` → Data exploration and insights
   * `Medical Insurance Forecast Model.ipynb` → Modeling and prediction

---

## Conclusion

This study successfully identified the key factors influencing medical insurance charges and built predictive models to estimate future costs. Ensemble methods, particularly Random Forest and Gradient Boosting, provided the most accurate forecasts.

**Future Work:**

* Incorporate additional health and lifestyle features for improved accuracy
* Explore deep learning models for higher-dimensional data
* Deploy the model as a web application for real-time insurance predictions

---
