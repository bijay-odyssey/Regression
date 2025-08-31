# **House Price Prediction**
This project includes building Regression Model and  optimizing it for predicting house prices.

---

## 📁 Project Structure

| File/Folder         | Description |
|---------------------|-------------|
| `EDA.ipynb`         | Basic EDA |
| `EDA2.ipynb`        | Detailed EDA |
| **`model.ipynb`**       | **Full EDA, Preprocessing, Pipelines, Model Training, Fine-Tuning, Evaluation** |
| `test.csv`          | Test Dataset |
| `train.csv`         | Train Dataset |
| `fine_tuned_models/`| Folder containing saved model pipelines: <br> &nbsp;&nbsp;• `GradientBoosting_model_pipeline.pkl` <br> &nbsp;&nbsp;• `Lasso_model_pipeline.pkl` <br> &nbsp;&nbsp;• `LinearRegression_model_pipeline.pkl` |

--- 

### `model.ipynb` — Main Notebook

This is the **core notebook** of the project. It covers the complete data science workflow from raw data to final model export.

#### EDA
- Initial data exploration and insights.

#### Preprocessing
- Handling missing values
- Encoding categorical features
- Scaling numerical features

#### Full Modeling
- Model training with multiple algorithms
- Hyperparameter tuning

#### Model Evaluation
Evaluation metrics used:
- MSE (Mean Squared Error)
- RMSE (Root Mean Squared Error)
- MAE (Mean Absolute Error)
- R² Score

#### Visualizations
- Residual Plot
- Actual vs. Predicted Plot
- Learning Curve (with R² score over training size)

#### Model Interpretation
- **Linear Models**: Feature coefficients
- **Tree-based Models**: Feature importance

#### Final Pipeline and Export
- Best model saved as `.pkl` file using joblib
- Includes preprocessing steps via pipeline

---

## Technologies & Tools Used

- Python 3.x
- Jupyter Notebook
- Pandas, NumPy
- Matplotlib, Seaborn
- Missingno
- Scipy
- Scikit-learn
- XGBoost / LightGBM (if used)
- Joblib
- Os
---
