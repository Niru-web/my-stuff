# 🗄️ SQL for Data Analysis

#sql #databases #queries #data-analyst #beginner

> 📖 **What is this?**
> SQL (Structured Query Language) is used to extract and manipulate data stored in relational databases. It's the #1 skill every data analyst must master.

---

## 🎯 Why SQL Matters

- 90% of company data lives in relational databases (SQL)
- Most data analyst job postings list SQL as a **required** skill
- Faster than Pandas for querying large datasets (millions of rows)
- Works with: PostgreSQL, MySQL, SQLite, BigQuery, Snowflake, Redshift

---

## 📦 Key Concepts

### 1. Basic Queries

```sql
SELECT column1, column2
FROM table_name
WHERE condition
ORDER BY column1 DESC
LIMIT 10;
```

- **SELECT** — choose which columns to return
- **FROM** — specify the table
- **WHERE** — filter rows by condition
- **ORDER BY** — sort results (ASC / DESC)
- **LIMIT** — restrict number of rows returned

### 2. Aggregations & Grouping

```sql
SELECT department, COUNT(*) AS headcount, AVG(salary) AS avg_salary
FROM employees
GROUP BY department
HAVING AVG(salary) > 60000;
```

- **COUNT(), SUM(), AVG(), MIN(), MAX()** — aggregate functions
- **GROUP BY** — group rows before aggregating
- **HAVING** — filter on aggregated values (like WHERE but post-aggregation)

### 3. Joins

```sql
-- INNER JOIN: only matching rows
SELECT e.name, d.department_name
FROM employees e
INNER JOIN departments d ON e.dept_id = d.id;
```

| Join Type | Returns |
|-----------|---------|
| INNER JOIN | Only rows that match in both tables |
| LEFT JOIN | All rows from left + matches from right |
| RIGHT JOIN | All rows from right + matches from left |
| FULL OUTER JOIN | All rows from both tables |

### 4. Subqueries & CTEs

```sql
-- CTE (Common Table Expression)
WITH high_earners AS (
    SELECT name, salary
    FROM employees
    WHERE salary > (SELECT AVG(salary) FROM employees)
)
SELECT * FROM high_earners ORDER BY salary DESC;
```

- **Subqueries** — SELECT inside SELECT
- **CTEs (WITH clause)** — named temporary result sets; cleaner than subqueries
- **CASE WHEN** — conditional logic inside queries

### 5. Window Functions

```sql
SELECT 
    name,
    department,
    salary,
    RANK() OVER (PARTITION BY department ORDER BY salary DESC) AS salary_rank,
    LAG(salary) OVER (ORDER BY hire_date) AS prev_salary
FROM employees;
```

- **ROW_NUMBER()** — unique row number per partition
- **RANK() / DENSE_RANK()** — rank with/without gaps for ties
- **LAG() / LEAD()** — access previous/next row value
- **SUM() OVER()** — running total

---

## 🌍 Real-World Examples

- **E-commerce:** Find top 10 customers by total lifetime spend
- **SaaS:** Calculate monthly active users (MAU) by product feature
- **Finance:** Flag all transactions above $10,000 in the last 30 days
- **HR:** Get headcount and average salary by department and seniority level

---

## 🛠️ Tools & Technologies

| Tool | Use Case |
|------|----------|
| SQLite + DB Browser | Free, local practice (zero setup) |
| PostgreSQL + pgAdmin | Industry-standard open-source DB |
| MySQL Workbench | Popular in web development |
| Google BigQuery | Cloud data warehouse (free tier available) |
| Snowflake / Redshift | Enterprise cloud data warehouses |
| SQLZoo / LeetCode | Practice problems online |
| Mode Analytics | SQL + visualization for analysts |

---

## ✅ Mini Practice Tasks

1. Install SQLite. Create a table `employees` with: `id`, `name`, `salary`, `department`
2. Insert 10 rows of dummy data
3. Write a query to find average salary by department
4. Use LEFT JOIN to match employees to a `projects` table
5. Use a window function to rank employees by salary within each department
6. Write a CTE that finds employees earning above the company average

```sql
-- Practice: Rank employees within department
SELECT 
    name,
    department,
    salary,
    RANK() OVER (PARTITION BY department ORDER BY salary DESC) AS dept_rank
FROM employees;

-- Practice: Employees above average salary (CTE)
WITH avg_sal AS (
    SELECT AVG(salary) AS company_avg FROM employees
)
SELECT e.name, e.salary
FROM employees e, avg_sal
WHERE e.salary > avg_sal.company_avg;
```

---

## 🔗 Internal Links

- [[03_Python_Programming|→ Python Programming]]
- [[05_Exploratory_Data_Analysis|→ Exploratory Data Analysis]]
- [[07_Machine_Learning|→ Machine Learning]]
- [[00_MAIN_ROADMAP|← Back to Roadmap]]

---

## ➡️ Next Step

You now know Python + SQL. Time to use both together on real datasets!

**→ [[05_Exploratory_Data_Analysis|Exploratory Data Analysis]]**

> 💡 **Interview Tip:** Window functions (RANK, LAG, LEAD, running totals) are asked in almost every data analyst interview. Master them — they separate good candidates from great ones.
