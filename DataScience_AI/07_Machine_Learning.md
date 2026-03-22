# 🤖 Machine Learning

#machine-learning #supervised #unsupervised #scikit-learn #xgboost #intermediate

> 📖 **What is this?**
> Machine Learning is teaching computers to learn patterns from data and make predictions — without being explicitly programmed for every scenario.

---

## 🎯 Why Machine Learning?

- Powers: Netflix recommendations, fraud detection, self-driving cars, voice assistants
- Automates complex decisions at massive scale (millions per second)
- Discovers patterns in data that humans can't see manually
- Core skill for any Data Science or AI Engineering role

---

## 📦 Key Concepts

### 1. Types of Machine Learning

**Supervised Learning** — learns from labeled data (input + correct output)
- **Regression** — predict a continuous number (e.g., house price, temperature)
- **Classification** — predict a category (e.g., spam/not spam, fraud/not fraud)

**Unsupervised Learning** — no labels; find hidden structure
- **Clustering** — group similar data points (K-Means, DBSCAN)
- **Dimensionality Reduction** — compress data (PCA, t-SNE, UMAP)

**Reinforcement Learning** — agent learns by receiving reward/punishment signals

### 2. Core Algorithms

| Algorithm | Type | Best For |
|-----------|------|----------|
| Linear Regression | Regression | Simple, interpretable baseline |
| Logistic Regression | Classification | Binary outcomes, interpretable |
| Decision Tree | Both | Easy to visualize and explain |
| Random Forest | Both | Robust, good out-of-the-box |
| XGBoost / LightGBM | Both | Top Kaggle algorithm, tabular data |
| SVM | Both | High-dimensional data |
| K-Nearest Neighbors | Both | Small datasets, no training needed |
| Naive Bayes | Classification | Text classification |
| K-Means | Clustering | Customer segmentation |
| PCA | Dimensionality | Reduce features, visualize data |

### 3. Model Evaluation

**Never evaluate on training data!**

**Regression Metrics:**
- **MAE** (Mean Absolute Error) — average absolute difference
- **RMSE** (Root Mean Squared Error) — penalizes large errors more
- **R-squared** — % of variance explained

**Classification Metrics:**
- **Accuracy** — % of correct predictions (misleading for imbalanced data!)
- **Precision** — of predicted positives, how many are truly positive?
- **Recall** — of all actual positives, how many did we catch?
- **F1-Score** — harmonic mean of precision and recall
- **ROC-AUC** — overall classifier performance across thresholds
- **Confusion Matrix** — true/false positives and negatives

### 4. Avoiding Overfitting

- **Overfitting** — model memorizes training data, fails on new data (high variance)
- **Underfitting** — model too simple, misses real patterns (high bias)
- **Cross-validation (k-fold)** — split data into k folds, train/validate each
- **Regularization:** Ridge (L2), Lasso (L1) — penalize large coefficients
- **Early Stopping** — stop training when validation performance stops improving
- **Hyperparameter Tuning:** `GridSearchCV`, `RandomizedSearchCV`, Optuna

### 5. The ML Pipeline

```
Raw Data
   ↓
EDA & Data Cleaning
   ↓
Feature Engineering & Encoding
   ↓
Train / Validation / Test Split
   ↓
Model Training
   ↓
Evaluation (cross-validation)
   ↓
Hyperparameter Tuning
   ↓
Final Evaluation on Test Set
   ↓
Model Deployment (→ MLOps)
```

---

## 🌍 Real-World Examples

- **Banking:** XGBoost predicts loan default probability with 95% AUC
- **Retail:** K-Means clusters customers into 5 buying personas for targeted marketing
- **Healthcare:** Random Forest predicts 30-day patient readmission risk
- **E-commerce:** Collaborative filtering recommends products (Amazon's "also bought")

---

## 🛠️ Tools & Technologies

- **Scikit-learn** — the standard Python ML library (every algorithm + pipelines)
- **XGBoost / LightGBM / CatBoost** — gradient boosting libraries
- **Pandas + NumPy** — data preparation
- **Matplotlib / Seaborn** — visualizing model results
- **SHAP** — explainable AI, understand feature importance
- **MLflow** — experiment tracking (see [[09_MLOps]])
- **Optuna** — hyperparameter optimization

```python
from sklearn.ensemble import RandomForestClassifier
from sklearn.model_selection import cross_val_score
from sklearn.metrics import classification_report
import numpy as np

# Train a Random Forest
model = RandomForestClassifier(n_estimators=100, random_state=42)
scores = cross_val_score(model, X_train, y_train, cv=5, scoring='f1')
print(f"CV F1 Score: {np.mean(scores):.3f} ± {np.std(scores):.3f}")

model.fit(X_train, y_train)
y_pred = model.predict(X_test)
print(classification_report(y_test, y_pred))
```

---

## ✅ Mini Practice Tasks

1. Train a Logistic Regression on the Iris dataset — print accuracy
2. Train a Random Forest on Titanic — aim for 80%+ accuracy
3. Plot a confusion matrix and calculate precision, recall, F1-score
4. Try XGBoost on the same dataset — compare performance
5. Use 5-fold cross-validation to evaluate your best model
6. Use SHAP to visualize which features your model finds most important

---

## 🔗 Internal Links

- [[01_Mathematics|→ Mathematics]]
- [[02_Statistics|→ Statistics]]
- [[05_Exploratory_Data_Analysis|→ Exploratory Data Analysis]]
- [[06_Econometrics|→ Econometrics]]
- [[08_Deep_Learning|→ Deep Learning]]
- [[09_MLOps|→ MLOps]]
- [[00_MAIN_ROADMAP|← Back to Roadmap]]

---

## ➡️ Next Step

You can build and evaluate ML models. Now go deeper with neural networks!

**→ [[08_Deep_Learning|Deep Learning]]**

> 💡 **Rule of Thumb:** Always start with simple models (Logistic Regression, Decision Tree). Complex models are only worth the added complexity if they significantly outperform simpler ones.
