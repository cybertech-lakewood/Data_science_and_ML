# Supervised Learning (A) — Customer Churn Prediction

A machine learning notebook that builds and evaluates multiple supervised learning models to predict customer churn for an investment bank.

---

## Problem Statement

Develop a predictive model to identify customers at risk of churning, enabling proactive retention strategies to minimise customer loss and maximise revenue growth.

---

## Dataset

**File:** `churn.xlsx`  
**Size:** 10,000 rows × 14 columns

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
| `Exited` | **Target** — 1 if customer churned, 0 otherwise |

> Columns `RowNumber`, `CustomerId`, and `Surname` were dropped as they have no predictive value.

---

## Models Covered

### 1. K-Nearest Neighbors (KNN)
A distance-based classifier that predicts churn by finding the K most similar customers.

**Key hyperparameters explored:**
- `n_neighbors`: 3, 5, 10, 20
- `weights`: uniform, distance
- `metric`: Euclidean, Manhattan, Minkowski, Chebyshev

### 2. Support Vector Machine (SVM)
Finds the optimal hyperplane that separates churned vs. retained customers.

**Key hyperparameters explored:**
- `C` (regularisation): 1.0, 10.0, 100.0, 1000.0
- `kernel`: rbf, linear, poly, sigmoid
- `gamma`: scale, auto, 0.1, 1.0

### 3. Decision Tree
A tree-based model that splits data on the most informative features.

### 4. Random Forest
An ensemble of decision trees for improved accuracy and robustness.

---

## Workflow

```
Load Data → Preprocess → Split (80/20) → Train → Evaluate → Save Model
```

**Preprocessing steps:**
- Label encoding and one-hot encoding for categorical features (`Geography`, `Gender`)
- Feature scaling with `MinMaxScaler`
- Train/test split: 80% train, 20% validation (`random_state=0`)

**Evaluation metrics:**
- Accuracy Score
- ROC-AUC Score
- Confusion Matrix
- Classification Report

---

## Results Summary

| Model | Accuracy | AUC Score |
|---|---|---|
| Random Forest (functional approach) | 86.85% | 0.862 |
| SVM (OOP approach) | 79.75% | 0.421 |

---

## Implementation Approaches

The notebook demonstrates two coding styles:

- **Functional approach** — modular functions (`load_data`, `preprocess_data`, `train_model`, `evaluate_model`, `save_model`)
- **OOP approach** — a `ChurnPrediction` class encapsulating the full pipeline

---

## Libraries Used

```python
pandas, numpy, matplotlib
scikit-learn (KNeighborsClassifier, SVC, DecisionTreeClassifier, RandomForestClassifier)
joblib
```


## Author

**Viena Atieno Ouma**  
BSc Software Engineering, Murang'a University of Technology  
[GitHub](https://github.com/cybertech-lakewood) · [LinkedIn](https://linkedin.com/in/viena-ouma) · veeviena2@gmail.com
