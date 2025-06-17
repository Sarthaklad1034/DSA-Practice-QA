<div align="center">

<h1>Fibonacci Number</h1>

</div>

---

## 📝 Problem Statement

The Fibonacci numbers, commonly denoted as `F(n)`, form a sequence, called the Fibonacci sequence, where each number is the sum of the two preceding ones, starting from 0 and 1. That is:

```
F(0) = 0, F(1) = 1  
F(n) = F(n - 1) + F(n - 2), for n > 1
```

Given an integer `n`, calculate `F(n)`.

---

## 🔍 Examples

<table>
<tr>
<th>Example</th>
<th>Input</th>
<th>Output</th>
<th>Explanation</th>
</tr>
<tr>
<td><strong>1</strong></td>
<td><code>n = 2</code></td>
<td><code>1</code></td>
<td><code>F(2) = F(1) + F(0) = 1 + 0 = 1</code></td>
</tr>
<tr>
<td><strong>2</strong></td>
<td><code>n = 3</code></td>
<td><code>2</code></td>
<td><code>F(3) = F(2) + F(1) = 1 + 1 = 2</code></td>
</tr>
<tr>
<td><strong>3</strong></td>
<td><code>n = 4</code></td>
<td><code>3</code></td>
<td><code>F(4) = F(3) + F(2) = 2 + 1 = 3</code></td>
</tr>
</table>

---

## ⚡ Constraints

```
0 <= n <= 30
```

---

## 🛠️ Solution Approaches

### Approach 1: Iterative Dynamic Programming

Use two variables to store the last two Fibonacci numbers and update them iteratively.

```python
class Solution(object):
    def fib(self, n):
        if n == 0 or n == 1:
            return n
        first = 0
        second = 1
        for i in range(1, n + 1):
            third = first + second
            first = second
            second = third
        return first
```

<div align="center">

**Time Complexity:** `O(n)` | **Space Complexity:** `O(1)`

</div>

---

### Approach 2: Top-Down with Memoization (Optimized)

This recursive solution uses memoization to store already computed values and avoids recomputation.

```python
class Solution(object):
    def fib(self, n):
        memo = {}
        def helper(x):
            if x in memo:
                return memo[x]
            if x == 0 or x == 1:
                return x
            memo[x] = helper(x - 1) + helper(x - 2)
            return memo[x]
        return helper(n)
```

### 🔍 Explanation

- Stores the result of each Fibonacci call to avoid redundant calculations.
- Reduces exponential time of naive recursion to linear time.

<div align="center">

**Time Complexity:** `O(n)` | **Space Complexity:** `O(n)` (due to recursion stack + memo dictionary)

</div>

---

## 🏆 Comparison

| Approach                    | Time       | Space | Pros                            | Cons                    |
|-----------------------------|------------|-------|---------------------------------|-------------------------|
| **Iterative DP**            | `O(n)`     | `O(1)`| Simple, efficient                | None                    |
| **Top-Down Memoization**    | `O(n)`     | `O(n)`| Cleaner recursion, avoids loops | Uses more memory stack  |

---

## 🧪 Test Cases

```python
def test():
    s = Solution()
    print(s.fib(0))   # 0
    print(s.fib(1))   # 1
    print(s.fib(2))   # 1
    print(s.fib(3))   # 2
    print(s.fib(4))   # 3
    print(s.fib(10))  # 55

test()
```

---

<div align="center">

`Math` • `Dynamic Programming` • `Memoization` • `Recursion` • `Easy`

---

*Happy Coding! 🚀*

</div>