# 🛠️ SQL, Python & ML Cheatsheet (Top Interview Questions)

When you reach the technical round, you will likely face HackerRank or LeetCode style questions, along with deep Machine Learning theory. Here are the most common patterns you MUST know.

## 🗄️ SQL Patterns

### 1. The "Top N" per Category (Window Functions)
*Question: Find the top 3 highest-paid employees in each department.*
```sql
WITH RankedEmployees AS (
    SELECT 
        name,
        department,
        salary,
        DENSE_RANK() OVER(PARTITION BY department ORDER BY salary DESC) as rnk
    FROM employees
)
SELECT name, department, salary 
FROM RankedEmployees 
WHERE rnk <= 3;
```
*Why they ask it:* It proves you understand `PARTITION BY` and the difference between `RANK()` and `DENSE_RANK()`.

### 2. The Rolling/Moving Average
*Question: Calculate the 7-day rolling average of daily sales.*
```sql
SELECT 
    date,
    sales,
    AVG(sales) OVER(ORDER BY date ROWS BETWEEN 6 PRECEDING AND CURRENT ROW) as rolling_7d_avg
FROM daily_sales;
```

### 3. The Cumulative Sum (Running Total)
*Question: Find the running total of revenue per month.*
```sql
SELECT 
    month,
    revenue,
    SUM(revenue) OVER(ORDER BY month ASC) as cumulative_revenue
FROM monthly_financials;
```

### 4. Self-Join for Hierarchical Data
*Question: Find the names of employees who earn more than their direct managers.*
```sql
SELECT e.name 
FROM employees e
JOIN employees m ON e.manager_id = m.id
WHERE e.salary > m.salary;
```

---

## 🐍 Python Patterns

### 1. Dictionary Comprehensions (Frequency Counting)
*Question: Given a string, count the frequency of each character.*
```python
text = "data engineering"
# The elegant way
freq = {char: text.count(char) for char in set(text)}
# The high-performance way (O(N))
from collections import Counter
freq = dict(Counter(text))
```

### 2. The Two Pointer Technique (Lists)
*Question: Given a sorted array, find two numbers that add up to a specific target in O(N) time.*
```python
def two_sum_sorted(arr, target):
    left, right = 0, len(arr) - 1
    while left < right:
        current_sum = arr[left] + arr[right]
        if current_sum == target:
            return (arr[left], arr[right])
        elif current_sum < target:
            left += 1
        else:
            right -= 1
    return None
```

### 3. The Sliding Window Technique
*Question: Find the maximum sum of any contiguous subarray of size `k`.*
```python
def max_sum_subarray(arr, k):
    max_sum = current_sum = sum(arr[:k])
    for i in range(len(arr) - k):
        current_sum = current_sum - arr[i] + arr[i+k]
        max_sum = max(max_sum, current_sum)
    return max_sum
```

---

## 🤖 Machine Learning Theory (Top 3 Questions)

### 1. "Explain the Bias-Variance Tradeoff."
**Answer:** Bias is the error from simplistic assumptions (Underfitting). Variance is the error from sensitivity to small fluctuations in the training set (Overfitting). The tradeoff is the tension between minimizing bias (getting closer to the training data) and minimizing variance (generalizing well to unseen data).

### 2. "How does a Random Forest actually work?"
**Answer:** It's an ensemble of Decision Trees. It uses **Bagging** (Bootstrap Aggregating) where each tree is trained on a random subset of the data, and at each split, it only considers a random subset of features. The final prediction is the majority vote (classification) or average (regression) of all trees. This reduces the high variance of individual decision trees.

### 3. "How do you handle highly imbalanced datasets?"
**Answer:** First, don't use Accuracy as a metric; use F1-Score, Precision-Recall AUC. Second, use algorithmic techniques like class weighting (giving higher penalty to mistakes on the minority class). Third, use data techniques like SMOTE (Synthetic Minority Over-sampling Technique) or random undersampling of the majority class.
