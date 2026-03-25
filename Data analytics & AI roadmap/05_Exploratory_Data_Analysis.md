# 🔍 Exploratory Data Analysis (EDA)

#eda #data-cleaning #visualization #feature-engineering #intermediate

> 📖 **What is this?**
> EDA is the process of investigating your data before modeling. You clean it, visualize it, and find patterns. It's what data analysts spend ~70% of their time on.

---

## 🎯 Why EDA Matters

- Understand your data before building models
- Catch errors: missing values, outliers, wrong data types
- Find patterns and insights that drive business decisions
- Choose the right features for machine learning models

---

## 📦 Key Concepts

### 1. Data Understanding

```python
df.shape          # rows and columns
df.dtypes         # data types per column
df.describe()     # mean, std, min, max for numeric cols
df.isnull().sum() # count missing values per column
df.duplicated().sum()  # count duplicate rows
df.nunique()      # unique values per column
```

### 2. Data Cleaning

- **Missing values:**
  - Numerical → fill with median (robust to outliers)
  - Categorical → fill with mode or "Unknown"
  - Drop rows/columns if >50% data is missing
- **Duplicates:** `df.drop_duplicates()`
- **Data type fixes:** `pd.to_datetime()`, `pd.to_numeric()`
- **Outlier detection:** IQR method, Z-scores
- **String cleaning:** `.str.lower()`, `.str.strip()`, `.str.replace()`

### 3. Univariate Analysis (Single Variable)

| Plot Type | Use For |
|-----------|---------|
| Histogram | Distribution of a numeric variable |
| Box Plot | Median, spread, outliers |
| Bar Chart | Frequency of categorical values |
| KDE Plot | Smooth distribution estimate |

```python
import seaborn as sns
import matplotlib.pyplot as plt

sns.histplot(df['Age'], bins=20, kde=True)
plt.title('Age Distribution')
plt.show()
```

### 4. Bivariate Analysis (Two Variables)

- **Scatter plot** — relationship between two numeric variables
- **Correlation matrix** — all pairwise correlations as a heatmap
- **Box plot by category** — numeric variable split by a category
- **Cross-tabulation:** `pd.crosstab(df['Sex'], df['Survived'])`

```python
# Correlation heatmap
import seaborn as sns
corr = df.select_dtypes(include='number').corr()
sns.heatmap(corr, annot=True, cmap='coolwarm', fmt='.2f')
plt.show()
```

### 5. Feature Engineering

- **Create new features** from existing columns
- **Encoding categoricals:** One-Hot (`pd.get_dummies()`), Label Encoding
- **Binning numerics:** `pd.cut()`, `pd.qcut()`
- **Date/time features:** extract year, month, day of week, hour
- **Interaction features:** multiply or combine two columns

```python
# Feature engineering examples
df['FamilySize'] = df['SibSp'] + df['Parch'] + 1
df['IsAlone'] = (df['FamilySize'] == 1).astype(int)
df['AgeGroup'] = pd.cut(df['Age'], bins=[0,12,18,60,100], 
                         labels=['Child','Teen','Adult','Senior'])
```

---

## 🌍 Real-World Examples

- **Banking:** Check for outliers in transaction amounts before fraud model training
- **Netflix:** EDA reveals watch time drops sharply after 3+ consecutive episodes
- **Retail:** 30% of revenue comes from just 5% of products (Pareto principle)
- **Healthcare:** Missing BMI data is not random — it's skewed toward certain demographics (bias!)

---

## 🛠️ Tools & Technologies

- **Pandas** — data loading, cleaning, transformation
- **Matplotlib & Seaborn** — static plots
- **Plotly** — interactive charts (great for dashboards)
- **ydata-profiling** — automated EDA report with one line of code
- **Sweetviz** — visual EDA report comparing datasets
- **Missingno** — visualize missing data patterns

```python
# Auto EDA report (one line!)
from ydata_profiling import ProfileReport
profile = ProfileReport(df, title="EDA Report")
profile.to_file("eda_report.html")
```

---

## ✅ Mini Practice Tasks

1. Download the Titanic dataset from Kaggle
2. Check: shape, dtypes, missing values, duplicates
3. Fill missing `Age` with median; drop rows with missing `Embarked`
4. Plot histograms for `Age` and `Fare` — note the skewness
5. Create a correlation heatmap — which features correlate with `Survived`?
6. Create a new feature: `FamilySize = SibSp + Parch + 1`
7. Generate a full EDA report using `ydata-profiling`

---

## 🔗 Internal Links

- [[03_Python_Programming|→ Python Programming]]
- [[02_Statistics|→ Statistics]]
- [[04_SQL_for_Data_Analysis|→ SQL for Data Analysis]]
- [[07_Machine_Learning|→ Machine Learning]]
- [[00_MAIN_ROADMAP|← Back to Roadmap]]

---

## ➡️ Next Step

You've mastered data exploration. Now let's add statistical rigor with Econometrics!

**→ [[06_Econometrics|Econometrics]]**

> 💡 **Golden Rule:** Never skip EDA before modeling. Garbage in = garbage out. Clean, well-understood data is the foundation of every good model.
