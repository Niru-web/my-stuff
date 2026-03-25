# 📊 Statistics for Data Science

#statistics #descriptive #inferential #hypothesis-testing #beginner

> 📖 **What is this?**
> Statistics is the science of collecting, analyzing, and interpreting data. It's how data scientists draw meaningful conclusions from raw numbers.

---

## 🎯 Why Statistics Matters

- Every data project involves statistical thinking
- A/B testing (used by every tech company) is pure statistics
- Understanding data distributions helps you choose the right model
- Hypothesis testing validates whether your findings are real or just noise

---

## 📦 Key Concepts

### 1. Descriptive Statistics

- **Mean** — average value
- **Median** — middle value (robust to outliers)
- **Mode** — most frequent value
- **Variance** — average squared distance from the mean
- **Standard Deviation** — square root of variance; same unit as data
- **Percentiles & Quartiles** — Q1, Q2, Q3; used in box plots
- **Skewness** — asymmetry of the distribution
- **Kurtosis** — how heavy the tails are

### 2. Probability Distributions

- **Normal Distribution** — bell curve; used in most statistical tests
- **Binomial Distribution** — yes/no outcomes (e.g., click or no click)
- **Poisson Distribution** — count of events per time period (e.g., website visits/hour)
- **Uniform Distribution** — every outcome equally likely
- **Central Limit Theorem** — sample means approach Normal as n increases

### 3. Inferential Statistics

- **Sampling** — using a subset to represent the full population
- **Confidence Intervals** — range where the true value likely falls (e.g., 95% CI)
- **Hypothesis Testing** — is the result real or just random chance?
- **p-value** — probability the result occurred by chance; p < 0.05 = significant
- **Type I Error** — false positive (reject true null hypothesis)
- **Type II Error** — false negative (fail to reject false null hypothesis)

### 4. Common Statistical Tests

| Test | When to Use |
|------|------------|
| t-test | Compare means of two groups |
| Chi-Square | Test relationships between categories |
| ANOVA | Compare means of 3+ groups |
| Pearson Correlation | Linear relationship between two numeric vars |
| Mann-Whitney U | Non-parametric alternative to t-test |

---

## 🌍 Real-World Examples

- **A/B Testing:** Netflix tests UI changes using hypothesis testing before global rollout
- **Election Polling:** Agencies use confidence intervals — "52% ± 3%"
- **Quality Control:** Manufacturing uses control charts to detect process drift
- **Drug Trials:** t-tests validate whether a new drug works better than placebo

---

## 🛠️ Tools & Technologies

- **Python:** `scipy.stats`, `statsmodels` — statistical tests and regression
- **Pandas:** `.describe()` for quick descriptive stats on any DataFrame
- **Seaborn / Matplotlib** — visualize distributions, box plots, violin plots
- **Pingouin** — user-friendly Python stats library
- **R** — still the gold standard in academic statistics

---

## ✅ Mini Practice Tasks

1. Load the Titanic dataset → compute mean, median, std of the `Age` column
2. Plot histograms for `Age` and `Fare` — describe the distribution shape
3. Run a t-test to compare `Age` between survivors and non-survivors
4. Calculate the 95% confidence interval for average passenger age
5. Find the Pearson correlation between `Fare` and `Survived`

```python
import pandas as pd
from scipy import stats

df = pd.read_csv('titanic.csv')

# Descriptive stats
print(df['Age'].describe())

# t-test: age of survivors vs non-survivors
survived = df[df['Survived']==1]['Age'].dropna()
not_survived = df[df['Survived']==0]['Age'].dropna()
t_stat, p_val = stats.ttest_ind(survived, not_survived)
print(f"p-value: {p_val:.4f}")

# 95% Confidence Interval
mean = df['Age'].mean()
se = stats.sem(df['Age'].dropna())
ci = stats.t.interval(0.95, len(df['Age'].dropna())-1, loc=mean, scale=se)
print(f"95% CI: {ci}")
```

---

## 🔗 Internal Links

- [[01_Mathematics|→ Mathematics]]
- [[05_Exploratory_Data_Analysis|→ Exploratory Data Analysis]]
- [[06_Econometrics|→ Econometrics]]
- [[07_Machine_Learning|→ Machine Learning]]
- [[00_MAIN_ROADMAP|← Back to Roadmap]]

---

## ➡️ Next Step

Great work! Now let's learn to code so you can apply these concepts on real data.

**→ [[03_Python_Programming|Python Programming]]**

> 💡 **Key Insight:** p-value < 0.05 means your result is statistically significant — less than 5% chance it happened by random luck.
