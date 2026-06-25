# 🛠️ SQL & Python Cheatsheet (Top Interview Questions)

When you reach the technical round, you will likely face HackerRank or LeetCode style questions. Here are the most common patterns you MUST know.

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

---

## 🐍 Python Patterns

### 1. Dictionary Comprehensions
*Question: Given a list of words, create a dictionary where the key is the word and the value is its length.*
```python
words = ["data", "science", "ai", "mentorship"]
word_lengths = {word: len(word) for word in words}
```

### 2. The Two Pointer Technique (Lists)
*Question: Given a sorted array, find two numbers that add up to a specific target.*
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
*Why they ask it:* It proves you can optimize O(N^2) naive nested loops down to O(N) time complexity.
