# Car Price Prediction — Regression Models Comparison

A Jupyter-based analysis comparing multiple regression models to predict car prices using features like make, model, year, engine size, mileage, fuel type, and transmission. Each model is explored and evaluated independently to showcase strengths, weaknesses, and insights.

---

##  Dataset Overview

- **Features**:  
  - Categorical: `Make`, `Model`, `Fuel Type`, `Transmission`  
  - Numeric: `Year`, `Engine Size`, `Mileage`  
- **Preprocessing**:  
  - One-hot encoded categorical columns using `pd.get_dummies(drop_first=True, dtype=int)`.  
  - Final dataset contains only numeric values for model compatibility.

---

##  Project Breakdown

### 1. **Linear Regression**
- **Goal**: Establish a performance baseline with a simple, interpretable model.
- **Highlights**:
  - Model Type: Ordinary least squares linear regression  
  - Results:
    - **Train R²** ≈ 0.84  
    - **Test R²** ≈ 0.81  
    - **MAE** ≈ 4.65k  
    - **MSE** ≈ 37M  
  - **Insight**: Solid baseline; captures general trends but may miss non-linearity.

---

### 2. **Ridge Regression**
- **Goal**: Combat potential overfitting and multicollinearity via L2 regularization.
- **Highlights**:
  - Penalty applied to shrink coefficients uniformly.
  - Performance nearly identical to Linear Regression.

---

### 3. **Lasso Regression**
- **Goal**: Introduce L1 regularization, enabling feature selection.
- **Highlights**:
  - Encourages sparsity—potentially more interpretable model.
  - Performed similarly to Ridge and Linear Regression.

---

### 4. **Stochastic Gradient Descent (SGD Regressor)**
- **Goal**: Scalable approach using iterative updates on large datasets.
- **Highlights**:
  - Much lower performance: 
    - **Test R²** ≈ 0.32  
    - **MSE** ≈ 133M  
  - **Conclusion**: Poor convergence; not ideal for this dataset.

---

### 5. **Support Vector Regressor (SVR)**
- **Goal**: Capture non-linear patterns with kernel-based regression.
- **Highlights**:
  - Moderate performance: **Test R²** ≈ 0.67, **MAE** ≈ 5.97k.  
  - Better than SGD but still behind tree-based models.

---

### 6. **Decision Tree Regressor**
- **Goal**: Fit complex, non-linear relationships with single-tree model.
- **Highlights**:
  - Overfits easily:
    - **Test R²** ≈ 0.56  
    - High MSE and MAE  
  - Lack of generalization on unseen data.

---

### 7. **K-Nearest Neighbors (KNN) Regressor**
- **Goal**: Predict price based on average of nearest neighbors.
- **Highlights**:
  - Decent performance: **Test R²** ≈ 0.74, **MSE** ≈ 50M.  
  - Outperformed some but still behind ensemble models.

---

### 8. **Gradient Boosting Regressor**
- **Goal**: Combine weak learners to iteratively improve model performance.
- **Highlights**:
  - Severe overfitting: Perfect train R² = 1.0, but **Test R²** ≈ 0.34.  
  - Doesn’t generalize well in current setup.

---

### 9. **Random Forest Regressor  —  *Best Performer***
- **Goal**: Leverage ensemble of decision trees for robust performance.
- **Highlights**:
  - **Train R²** ≈ 0.94  
  - **Test R²** ≈ 0.834  
  - **MAE** ≈ 4.15k  
  - **MSE** ≈ 32M (lowest)  
  - **Conclusion**: Best trade-off between bias and variance—clear winner.

---

##  Performance Summary

| Model                     | Test R² | MAE (k) | MSE (M) |
|---------------------------|---------|---------|---------|
| Random Forest Regressor   | **0.834** | **4.15** | **32.37** |
| Linear / Ridge / Lasso    | ~0.81   | ~4.65  | ~37.2     |
| KNN Reg.                  | ~0.74   | ~5.10  | ~50.2     |
| SVR                       | ~0.67   | ~5.97  | ~63.4     |
| Decision Tree             | ~0.56   | ~6.87  | ~85.2     |
| SGD Regressor             | ~0.32   | ~9.39  | ~133.3    |
| Gradient Boosting         | ~0.34   | ~8.68  | ~129.0    |

---

##  Visual Insights
- Scatter plots (Actual vs. Predicted) to visually assess model alignment with the ideal 45° line.
- Optional bar chart comparing Test R² scores across all models.

---

##  How to Run It

```bash
git clone https://github.com/1Omarelalfy1122/Regression.git
cd Regression/"Car Price Prediction"
pip install -r requirements.txt
jupyter notebook
