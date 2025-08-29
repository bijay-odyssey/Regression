### 📊 Regression Machine Learning Projects

Welcome to my portfolio of machine learning projects focused on **Regression tasks**. This repository serves as a central hub for various datasets and models I've developed. Each sub-directory contains a complete project, from exploratory data analysis (EDA) and preprocessing to model training, fine tuning and evaluation.

It includes wide range of Regression techniques applied to different real-world problems.

---

### 📂 Repository Structure

The projects are organized into sub-directories based on the dataset used. Each project folder is self-contained and includes:
- **Jupyter Notebooks**: Files documenting the full machine learning workflow.
- **Model Files**: Saved fine tuned models, pipelines, and scalers (`.joblib` or `.pkl`).
- **Data Files**: The dataset used for the project.

List of the current and planned projects in this repository:

| Project Directory | Description | Status |
| :--- | :--- | :--- |
| `housePricesModel/` | Predicting House's  SalePrice. | **Complete** |




---

### 🚀 Projects Overview

Click on the links below to navigate to the individual project directories for a detailed breakdown of each analysis.

#### **[https://github.com/bijay-odyssey/Regression/tree/main/housePricesModel)**

* **Objective**: To build Regression model that predicts House Price
* **Key Techniques**:
    * **ExploratoryDataAnalysis**: Data Visualization and Anaysis.
    * **Preprocessing Pipelines**: Using `ColumnTransformer` for combining encoder, imputer.
    * **Model Comparison**: Training and evaluating **LinearRegression,
    Ridge, Lasso, RandomForestRegressor, GradientBoostingRegressor**
* **Model Evaluation**: Utilizing **mean_squared_error, mean_absolute_error, r2_score, Learning curve with R2**,  for model Evaluation with Visuals like **Residual Plot and Actual vs Predicted Plot**.
* **Hyperparameter Tuning**: Model Optimization by fine tuning with paramters using **RandomizedSearchCV**
* **Model Interpretation**: Interpretation based on **Linear models** and **Tree based models** showcasing feature importance
---

### 🛠️ Technologies and Libraries

* **Languages**: Python in notebook
* **Libraries**: `pandas`, `numpy`, `scikit-learn`, `matplotlib`, `seaborn`, `joblib`, `os`

