# 🐍 Python Programming for Data Science

#python #pandas #numpy #matplotlib #coding #beginner

> 📖 **What is this?**
> Python is the #1 programming language for data science and AI. It's beginner-friendly, incredibly powerful, and has a massive ecosystem of libraries for every task.

---

## 🎯 Why Python?

- Most popular data science language — used at Google, Netflix, Uber, Amazon
- Huge library ecosystem: NumPy, Pandas, Scikit-learn, TensorFlow, PyTorch
- Easy to read and write — great first language for beginners
- Works for everything: data analysis, ML, web APIs, automation, scripting

---

## 📦 Key Concepts

### 1. Python Basics

- **Variables & Data Types:** `int`, `float`, `str`, `bool`, `list`, `dict`, `tuple`, `set`
- **Conditionals:** `if / elif / else`
- **Loops:** `for`, `while`
- **Functions:** `def`, `return`, `*args`, `**kwargs`
- **List Comprehensions:** `[x*2 for x in range(10)]`
- **File I/O:** reading/writing CSV, JSON, TXT files
- **Error Handling:** `try / except / finally`

### 2. NumPy — Numerical Computing

- Arrays and matrices (10–100x faster than Python lists)
- Math operations: `np.sum()`, `np.mean()`, `np.std()`, `np.dot()`
- Reshaping: `.reshape()`, `.flatten()`, `.T` (transpose)
- Slicing: `arr[0:5]`, `arr[:, 1]` (all rows, column 1)
- Broadcasting — operations on arrays of different shapes

### 3. Pandas — Data Manipulation

- **DataFrame** — a table of data (like Excel, but in Python)
- **Loading data:** `pd.read_csv()`, `pd.read_excel()`, `pd.read_json()`
- **Inspection:** `.head()`, `.info()`, `.describe()`, `.shape`
- **Filtering:** `df[df['Age'] > 25]`
- **Selecting:** `df[['col1', 'col2']]`, `df.loc[]`, `df.iloc[]`
- **Groupby:** `df.groupby('City')['Sales'].sum()`
- **Merging:** `pd.merge(df1, df2, on='id')`, `pd.concat()`
- **Missing values:** `.isnull()`, `.fillna()`, `.dropna()`
- **Apply:** `df['col'].apply(lambda x: x*2)`

### 4. Matplotlib & Seaborn — Visualization

- **Matplotlib:** line plots, bar charts, scatter plots, histograms
- **Seaborn:** heatmaps, violin plots, pair plots — built on Matplotlib
- **Customizing:** titles, axis labels, colors, figure size, legends
- **Subplots:** `fig, axes = plt.subplots(1, 2)`

---

## 🌍 Real-World Examples

- **Pandas:** Cleaning messy raw sales data before analysis
- **NumPy:** Matrix multiplication in a recommendation engine
- **Matplotlib:** Building charts for an executive quarterly report
- **Python scripts:** Automating daily ETL (Extract-Transform-Load) jobs

---

## 🛠️ Tools & Setup

- **IDE:** VS Code (recommended) or Jupyter Notebook / JupyterLab
- **Environment:** Anaconda (easiest setup) or `pip` + `virtualenv`
- **Install libraries:** `pip install pandas numpy matplotlib seaborn`
- **Google Colab** — free cloud Jupyter notebooks, zero local setup needed
- **Kaggle Notebooks** — free GPU + built-in datasets

---

## ✅ Mini Practice Tasks

1. Install Python and open Jupyter Notebook. Print `"Hello, Data Science!"`
2. Create a NumPy array of 10 random numbers → find mean, max, and min
3. Load the Titanic CSV using Pandas → show first 5 rows with `.head()`
4. Filter: find all passengers older than 40
5. Plot a bar chart of survival rate by passenger class using Matplotlib
6. Write a function that accepts a DataFrame column and returns mean, median, and std

```python
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt

# NumPy basics
arr = np.random.randint(1, 100, 10)
print(f"Mean: {arr.mean()}, Max: {arr.max()}, Min: {arr.min()}")

# Pandas basics
df = pd.read_csv('titanic.csv')
print(df.head())
print(df[df['Age'] > 40][['Name', 'Age', 'Survived']])

# Visualization
survival_by_class = df.groupby('Pclass')['Survived'].mean()
survival_by_class.plot(kind='bar', title='Survival Rate by Class', color='steelblue')
plt.ylabel('Survival Rate')
plt.tight_layout()
plt.show()
```

---

## 🔗 Internal Links

- [[01_Mathematics|→ Mathematics]]
- [[02_Statistics|→ Statistics]]
- [[04_SQL_for_Data_Analysis|→ SQL for Data Analysis]]
- [[05_Exploratory_Data_Analysis|→ Exploratory Data Analysis]]
- [[00_MAIN_ROADMAP|← Back to Roadmap]]

---

## ➡️ Next Step

You can code in Python now — let's add SQL to your toolkit!

**→ [[04_SQL_for_Data_Analysis|SQL for Data Analysis]]**

> 💡 **Pro Tip:** Practice coding every single day, even if just for 20 minutes. Use Kaggle datasets for real practice problems. Consistency beats intensity.
