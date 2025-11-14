# 📊 Regression Machine Learning Projects

Welcome to my portfolio of **Regression-focused machine learning projects**. This repository serves as a central hub for projects where I explore real-world datasets, perform detailed exploratory data analysis (EDA), preprocess data, implement various regression models, and evaluate predictive performance.

This collection reflects a **learn-while-doing approach**, emphasizing hands-on application of regression techniques, interpretation of model results, and improvement through hyperparameter tuning. Each project is self-contained and showcases a complete workflow from data exploration to model evaluation.

---

##  Key Features & Insights (Summary)

| Project                    | Key Features                                                           | Most Important Predictors         | Best Performing Models           | Key Insight                                                                                                |
| -------------------------- | ---------------------------------------------------------------------- | --------------------------------- | -------------------------------- | ---------------------------------------------------------------------------------------------------------- |
| Medical Insurance Forecast | Age, Sex, BMI, Children, Smoker, Region                                | Smoking, Age, BMI                 | Gradient Boosting, Random Forest | Ensemble methods handle non-linear relationships well; smoking status is a major cost driver.              |
| House Prices Model         | LotArea, OverallQual, YearBuilt, Neighborhood, GarageCars, TotalBsmtSF | OverallQual, GrLivArea, YearBuilt | Gradient Boosting, Random Forest | Tree-based models outperform linear regression; feature importance reveals property quality drives prices. |

This table allows quick understanding of **each project's scope, predictive factors, and outcomes**, ideal for a research portfolio.

---

##  Repository Overview

The repository currently includes two major projects:

| Project Directory             | Objective                                                                     | Status   |
| ----------------------------- | ----------------------------------------------------------------------------- | -------- |
| `Medical Insurance Forecast/` | Predicting medical insurance charges based on demographic and health features | Complete |
| `housePricesModel/`           | Predicting house sale prices using property and location features             | Complete |

Each project folder includes:

* **Jupyter Notebooks:** Documenting the full machine learning workflow from EDA to model evaluation
* **Model Files:** Saved models, pipelines, and scalers (`.joblib` or `.pkl`)
* **Data Files:** Dataset used for analysis

---

## 📂 Projects Breakdown

### 1. Medical Insurance Forecast

**Objective:** Predict insurance charges based on age, BMI, smoking status, and other factors.

**Workflow:**

1. **Exploratory Data Analysis (EDA):** Visualizations, correlations, statistical tests (T-test, ANOVA).
2. **Preprocessing:** Outlier removal, scaling, and categorical encoding.
3. **Modeling:** Compared multiple regression techniques including Linear Regression, Ridge, Lasso, Huber Regression, Random Forest, and Gradient Boosting.
4. **Feature Importance:** Smoking, age, and BMI identified as the most influential features.
5. **Evaluation:** Model performance assessed via RMSE, R², residual plots, and learning curves.

**Key Insight:** Ensemble methods (Random Forest & Gradient Boosting) outperformed linear models, demonstrating robustness in predicting insurance costs.

---

### 2. House Prices Model

**Objective:** Predict house sale prices using property and neighborhood attributes.

**Workflow:**

1. **EDA:** Data visualization, feature correlations, handling missing values.
2. **Preprocessing:** Pipelines built with `ColumnTransformer` for combined encoding, imputation, and scaling.
3. **Model Comparison:** Linear Regression, Ridge, Lasso, Random Forest, and Gradient Boosting models evaluated.
4. **Evaluation Metrics:** Mean Squared Error (MSE), Mean Absolute Error (MAE), R² Score, Residual Plots, Actual vs Predicted plots.
5. **Hyperparameter Tuning:** Optimization using `RandomizedSearchCV` for best model performance.
6. **Feature Interpretation:** Feature importance analyzed for both linear and tree-based models.

**Key Insight:** Ensemble tree-based models captured complex non-linear relationships, outperforming linear models for house price prediction.

---

##  Technologies & Libraries

* **Programming Language:** Python
* **Libraries:** pandas, numpy, scikit-learn, matplotlib, seaborn, joblib, os
* **Development Environment:** Jupyter Notebook

---

## 📁 Repository Structure

```
Regression/
│
├── Medical Insurance Forecast/
│   ├── EDA.ipynb                        # Exploratory Data Analysis
│   ├── Medical Insurance Forecast Model.ipynb  # Modeling & evaluation
│   
│
├── housePricesModel/
│   ├── EDA.ipynb                        # Exploratory Data Analysis
│   ├── HousePriceModel.ipynb            # Modeling & evaluation
│  
│
└── README.md                             # Project documentation
```

---

##  Learning & Research Focus

This repository demonstrates:

* **Hands-on application of regression techniques** for real-world problems.
* **Data-driven decision making:** Statistical tests, feature importance, and correlation analysis.
* **Model evaluation & optimization:** Selecting best-performing models using metrics and hyperparameter tuning.
* **Research mindset:** Documenting workflow, interpreting results, and drawing actionable insights.

This approach mirrors **student-led research projects**, emphasizing both practical implementation and analytical understanding of predictive modeling.

---

##  How to Use

1. Clone the repository:

```bash
git clone <repository-url>
```


2. Open Jupyter notebooks and run sequentially:

   * `EDA.ipynb` → Explore data and insights
   * `Model.ipynb` → Preprocessing, modeling, evaluation, and tuning

---

