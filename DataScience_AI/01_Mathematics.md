# 📐 Mathematics for Data Science

#mathematics #linear-algebra #calculus #probability #beginner

> 📖 **What is this?**
> Mathematics is the language of data science. It helps you understand how ML algorithms work under the hood.

---

## 🎯 Why Mathematics Matters

- Machine learning algorithms are mathematical equations
- Statistics is built on probability theory
- Data transformations use linear algebra
- Optimization (training models) uses calculus

---

## 📦 Key Concepts

### 1. Linear Algebra

- **Vectors** — 1D array of numbers (e.g., a single data row)
- **Matrices** — 2D array of numbers (e.g., a dataset)
- **Matrix Multiplication** — core operation used in neural networks
- **Eigenvalues / Eigenvectors** — used in PCA for dimensionality reduction
- **Dot Product** — measures similarity between vectors
- **Transpose** — flip rows and columns of a matrix

### 2. Calculus

- **Derivatives** — rate of change (the slope of a curve)
- **Gradient** — multi-variable derivative; direction of steepest ascent
- **Chain Rule** — used in backpropagation to compute gradients
- **Gradient Descent** — how models learn by minimizing loss step by step
- **Partial Derivatives** — derivative with respect to one variable at a time

### 3. Probability

- **Probability** — likelihood of an event occurring (0 to 1)
- **Conditional Probability** — P(A | B): probability of A given B occurred
- **Bayes' Theorem** — update beliefs when new evidence arrives
- **Distributions** — Normal, Binomial, Poisson, Uniform
- **Expected Value** — weighted average outcome
- **Variance & Standard Deviation** — spread of a distribution

---

## 🌍 Real-World Examples

- **Linear Algebra:** Google's PageRank uses matrix operations on the web graph
- **Calculus:** Training a neural network uses gradient descent to minimize error
- **Probability:** Spam filters use Bayes' Theorem to classify emails
- **Matrices:** Images are stored as pixel matrices — CNNs process them with matrix ops

---

## 🛠️ Tools & Resources

- **NumPy** — Python library for fast matrix/vector operations
- **SymPy** — Python symbolic math (compute derivatives analytically)
- **Khan Academy** — free, beginner-friendly math courses
- **3Blue1Brown (YouTube)** — beautiful visual explanations of linear algebra & calculus
- **Book:** *Mathematics for Machine Learning* (free PDF available online)

---

## ✅ Mini Practice Tasks

1. Create a 3×3 matrix in NumPy and multiply it by another matrix
2. Calculate the derivative of `f(x) = x² + 3x` using SymPy
3. Simulate 1000 coin flips in Python — calculate probability of heads
4. Plot a Normal distribution using Matplotlib
5. Implement gradient descent from scratch to minimize `y = x²`

```python
import numpy as np

# Matrix multiplication
A = np.array([[1,2],[3,4]])
B = np.array([[5,6],[7,8]])
print(np.dot(A, B))

# Gradient descent for y = x^2
x = 10.0
lr = 0.1
for _ in range(50):
    grad = 2 * x
    x -= lr * grad
print(f"Minimum at x = {x:.4f}")
```

---

## 🔗 Internal Links

- [[02_Statistics|→ Statistics]]
- [[07_Machine_Learning|→ Machine Learning]]
- [[08_Deep_Learning|→ Deep Learning]]
- [[00_MAIN_ROADMAP|← Back to Roadmap]]

---

## ➡️ Next Step

You've built your math foundation. Now learn how to apply it to data!

**→ [[02_Statistics|Statistics]]**

> 💡 **Beginner Tip:** Don't try to master all math before coding. Learn math concepts as you need them — just-in-time learning is more effective.
