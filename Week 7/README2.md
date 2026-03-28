# Supervised Learning (B) - Gradient Boosting for Customer Churn Prediction

A continuation of the Supervised Learning (A) notebook, extending the churn prediction pipeline with advanced gradient boosting algorithms and automated hyperparameter tuning.

---

## Problem Statement

Predict customer churn at an investment bank using gradient boosting models, with a focus on optimising model performance through systematic hyperparameter search.

---

## Dataset

**File:** `churn.csv`  
**Size:** 10,000 rows × 14 columns  
**Source:** Mounted from Google Drive (`/content/drive/My Drive/Churn Project/churn.csv`)

**Target variable:** `Exited` — 1 if the customer churned, 0 otherwise.

**Features used:**

| Feature | Description |
|---|---|
| `CreditScore` | Customer credit score |
| `Geography` | Customer location (France, Spain, Germany) |
| `Gender` | Customer gender |
| `Age` | Customer age |
| `Tenure` | Years as a bank client |
| `Balance` | Account balance |
| `NumOfProducts` | Number of bank products held |
| `HasCrCard` | Whether the customer has a credit card |
| `IsActiveMember` | Whether the customer is an active member |
| `EstimatedSalary` | Estimated annual salary |

---

## Models Covered

### 1. XGBoost (eXtreme Gradient Boosting)
Builds an ensemble of decision trees sequentially, each correcting the errors of the previous one.

**Key hyperparameters explored:**
- `n_estimators`: 100, 200, 500, 1000
- `learning_rate`: 0.001, 0.01, 0.1, 0.2, 0.3
- `max_depth`: 3, 6, 9, 12
- `min_child_weight`, `gamma`, `subsample`, `colsample_bytree`
- `reg_alpha` (L1), `reg_lambda` (L2)

### 2. LightGBM (Light Gradient Boosting Machine)
Microsoft's efficient, distributed gradient boosting framework designed for speed and scalability.

**Key hyperparameters explored:**
- `n_estimators`: 100, 200, 500, 1000
- `learning_rate`: 0.01, 0.05, 0.1, 0.2
- `num_leaves`: 31, 50, 70, 100, 255
- `max_depth`, `min_data_in_leaf`, `bagging_fraction`, `feature_fraction`
- `lambda_l1` (L1), `lambda_l2` (L2)

---

## Hyperparameter Tuning Strategies

### GridSearchCV
Exhaustively tests every combination in a defined parameter grid. More thorough but computationally expensive.

### RandomizedSearchCV
Samples a fixed number of parameter settings from defined distributions (`scipy.stats.uniform`, `scipy.stats.randint`). Faster and often finds competitive results with `n_iter=50`.

Both strategies use `scoring='roc_auc'` and 3-fold cross-validation (`cv=3`).

---

## Workflow

```
Load Data (CSV) → Preprocess → StandardScaler → Split (80/20) → Train + Tune → Evaluate → Save Model
```

**Preprocessing steps:**
- One-hot encoding for `Geography` and `Gender` via `pd.get_dummies`
- Feature scaling with `StandardScaler`
- Train/test split: 80% train, 20% validation (`random_state=0`)

**Evaluation metrics:**
- Accuracy Score
- ROC-AUC Score

---

## Results Summary

| Model | Approach | Tuning | Accuracy | AUC Score |
|---|---|---|---|---|
| XGBoost | OOP | None (default) | 85.65% | 0.8545 |
| XGBoost | Procedural | GridSearchCV | 86.65% | 0.8751 |
| XGBoost | Procedural | RandomizedSearchCV | 86.45% | 0.8759 |
| LightGBM | OOP | None (default) | 85.90% | 0.8672 |
| LightGBM | Procedural | GridSearchCV | 86.50% | 0.8759 |

> **Best overall:** XGBoost with RandomizedSearchCV and LightGBM with GridSearchCV both achieved an AUC of ~0.876.

---

## Implementation Approaches

The notebook demonstrates two coding styles applied to both models:

- **OOP approach** — a `ChurnPrediction` class with methods for loading, preprocessing, splitting, training, evaluating, and saving the model
- **Procedural approach** — modular functions (`load_data`, `preprocess_data`, `train_model_xgb/lgb`, `evaluate_model`, `save_model`) with hyperparameter tuning integrated into the training step

---

## Libraries Used

```python
pandas, matplotlib
scikit-learn (GridSearchCV, RandomizedSearchCV, StandardScaler, train_test_split)
xgboost, lightgbm
scipy.stats (uniform, randint)
joblib, tensorflow
```


## Relationship to Supervised Learning (A)

This notebook is Part B of the supervised learning series. Part A covers baseline models (KNN, SVM, Decision Tree, Random Forest) on the same churn dataset. Part B advances the pipeline with gradient boosting and systematic hyperparameter search.

| Notebook | Models |
|---|---|
| Supervised Learning (A) | KNN, SVM, Decision Tree, Random Forest |
| Supervised Learning (B) | XGBoost, LightGBM + GridSearchCV / RandomizedSearchCV |

---

## Author

**Viena Atieno Ouma**  
BSc Software Engineering, Murang'a University of Technology  
[GitHub](https://github.com/cybertech-lakewood) · [LinkedIn](https://linkedin.com/in/viena-ouma) · veeviena2@gmail.com
