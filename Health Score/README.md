# 🩺 Health Score Prediction — Regression Models Comparison

A Jupyter-based analysis comparing multiple regression models to predict Health Score
based on lifestyle and physiological features (age, BMI, exercise, sleep, smoking, alcohol, diet).

Each model is trained, tested, and compared individually.

---

## 📊 Dataset Overview

Features:
  - Numeric: Age, BMI, Exercise Hours, Sleep Hours, Smoking, Alcohol Consumption, Diet Score
  - Target: Health Score

Preprocessing:
  - Dataset already numeric
  - Normalization + Train/Test Split

---

## ⚙️ Models Tested

1. Linear Regression
   - Baseline model (OLS)
   - Test R² ≈ 0.72 | MSE ≈ 37
   - Solid baseline, misses non-linear effects

2. Ridge Regression
   - L2 regularization
   - Similar performance to Linear Regression

3. Lasso Regression
   - L1 regularization (feature selection)
   - Similar performance to Ridge

4. SGD Regressor
   - Iterative updates
   - Test R² ≈ 0.40 | High MSE
   - Poor convergence, not suitable

5. SVR
   - Kernel-based regression
   - Test R² ≈ 0.68
   - Moderate performance, heavier computation

6. Decision Tree Regressor
   - Non-linear splits
   - Test R² ≈ 0.55 | Overfits training data

7. KNN Regressor
   - Neighborhood-based predictions
   - Test R² ≈ 0.70 | MSE ≈ 41
   - Decent, but sensitive to scaling

8. Gradient Boosting Regressor
   - Sequential learners
   - Test R² ≈ 0.58 | MSE ≈ 55
   - Overfitting issues

9. Random Forest Regressor (Best Performer)
   - Ensemble of decision trees
   - Train R² ≈ 0.94 | Test R² ≈ 0.80
   - Lowest MSE (~30s)
   - Best trade-off between bias and variance

---

## 📈 Performance Summary

| Model                   | Test R² | MSE   |
|--------------------------|---------|-------|
| Random Forest Regressor | **0.80** | ~30   |
| Linear / Ridge / Lasso  | ~0.72   | ~37   |
| KNN Regressor           | ~0.70   | ~41   |
| SVR                     | ~0.68   | ~45   |
| Gradient Boosting       | ~0.58   | ~55   |
| Decision Tree           | ~0.55   | ~60   |
| SGD Regressor           | ~0.40   | High  |

---

## ▶️ Run the Project

```bash
git clone https://github.com/1Omarelalfy1122/Regression.git
cd Regression/"Health Score"
jupyter notebook
