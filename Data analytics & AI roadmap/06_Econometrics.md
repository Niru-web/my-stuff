# 📈 Econometrics

#econometrics #regression #causality #time-series #intermediate

> 📖 **What is this?**
> Econometrics applies statistics to economic and business data. It answers not just "what is correlated?" but **"what actually causes what?"** — the foundation of causal inference.

---

## 🎯 Why Econometrics Matters

- Helps answer causal questions: *Does X cause Y?* not just *Is X correlated with Y?*
- Used in business analytics, policy evaluation, and rigorous A/B testing
- Bridges the gap between statistics and machine learning
- Required in data science roles in finance, consulting, economics, and policy

---

## 📦 Key Concepts

### 1. Linear Regression (OLS)

```
Y = β₀ + β₁X₁ + β₂X₂ + ... + ε
```

- **OLS (Ordinary Least Squares)** — fits a line that minimizes squared errors
- **Coefficients (β)** — how much Y changes for a 1-unit increase in X
- **R-squared** — % of variance in Y explained by the model (0 to 1)
- **p-value** — is each coefficient statistically significant?
- **Residuals (ε)** — difference between actual and predicted values

**OLS Assumptions (must check!):**
- Linearity — relationship between X and Y is linear
- No multicollinearity — predictors not highly correlated with each other
- Homoscedasticity — residual variance is constant
- No autocorrelation — residuals are independent
- Normality of residuals

### 2. Multiple Regression

- Add multiple predictors: controls for confounders
- **Interaction terms:** does the effect of X₁ depend on X₂?
- **VIF (Variance Inflation Factor)** — detect multicollinearity (VIF > 5 = problem)
- **Adjusted R-squared** — penalizes for adding useless variables

### 3. Diagnostic Tests

| Issue | Test | Fix |
|-------|------|-----|
| Heteroscedasticity | Breusch-Pagan test | Robust standard errors |
| Autocorrelation | Durbin-Watson test | Add lagged variables |
| Non-normal residuals | Shapiro-Wilk, Q-Q plot | Transform the variable |
| Outliers | Cook's Distance | Investigate and remove |

### 4. Time Series Analysis

- **Components:** Trend + Seasonality + Cyclical + Random
- **Stationarity** — mean and variance are constant over time (required for ARIMA)
- **ADF Test** — Augmented Dickey-Fuller test for stationarity
- **Differencing** — make non-stationary series stationary
- **ACF / PACF plots** — determine AR and MA parameters
- **ARIMA(p, d, q)** — AutoRegressive Integrated Moving Average model
- **SARIMA** — ARIMA with seasonal component

### 5. Causal Inference Methods

| Method | When to Use |
|--------|------------|
| RCT (Randomized Controlled Trial) | Gold standard — random assignment |
| Instrumental Variables (IV) | Observational data + a good instrument |
| Difference-in-Differences (DiD) | Natural experiments with before/after data |
| Regression Discontinuity (RDD) | Treatment assigned at a threshold |
| Propensity Score Matching | Match treated/control on observable characteristics |

---

## 🌍 Real-World Examples

- **Marketing:** Does increasing ad spend *cause* more sales? (IV analysis)
- **HR Policy:** Did diversity training *reduce* bias? (DiD study)
- **Demand Forecasting:** ARIMA models forecast retail demand and inventory needs
- **Minimum Wage:** Did a wage increase *cause* unemployment? (RDD at policy threshold)
- **Drug Approval:** Clinical trials use regression to control for patient demographics

---

## 🛠️ Tools & Technologies

- **Python:** `statsmodels` — OLS, ARIMA, hypothesis tests
- **Python:** `linearmodels` — IV regression, panel data
- **Python:** `scipy.stats` — statistical tests
- **Python:** `pmdarima` — auto ARIMA parameter selection
- **R:** `lm()`, `plm`, `forecast` packages — academic standard
- **Excel:** Data Analysis ToolPak for basic regression

```python
import statsmodels.api as sm
import pandas as pd

# OLS Regression
X = df[['Size_sqft', 'Bedrooms', 'Age']]
y = df['Price']
X = sm.add_constant(X)  # adds intercept
model = sm.OLS(y, X).fit()
print(model.summary())
```

---

## ✅ Mini Practice Tasks

1. Run OLS regression in Python: predict house price from size and bedrooms
2. Interpret: coefficients, R-squared, and p-values from the summary output
3. Check for heteroscedasticity by plotting residuals vs. fitted values
4. Download monthly sales data → build an ARIMA model to forecast next 3 months
5. Research: Find one real study that used the DiD method — what did it find?

---

## 🔗 Internal Links

- [[02_Statistics|→ Statistics]]
- [[01_Mathematics|→ Mathematics]]
- [[05_Exploratory_Data_Analysis|→ Exploratory Data Analysis]]
- [[07_Machine_Learning|→ Machine Learning]]
- [[00_MAIN_ROADMAP|← Back to Roadmap]]

---

## ➡️ Next Step

Econometrics gave you the "why." Now scale up with Machine Learning for predictive power!

**→ [[07_Machine_Learning|Machine Learning]]**

> 💡 **Key Insight:** Correlation ≠ Causation. Ice cream sales and drowning rates both rise in summer — they're correlated, but the true cause is the weather, not the ice cream.
