
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

### Approach 1: Iterative Dynamic Programming (Java)

Use two variables to store the last two Fibonacci numbers and update them iteratively.

```java
class Solution {
    public int fib(int n) {
        if (n == 0 || n == 1) return n;
        int first = 0;
        int second = 1;
        for (int i = 1; i <= n; i++) {
            int third = first + second;
            first = second;
            second = third;
        }
        return first;
    }
}
```

<div align="center">

**Time Complexity:** `O(n)` | **Space Complexity:** `O(1)`

</div>

---

### 💡 Explanation

- We use two variables `first` and `second` to hold the last two values in the Fibonacci sequence.
- The loop iterates from `1` to `n`, updating these two values each time.
- We return the variable `first`, which holds the `n-th` Fibonacci number at the end.

---

### 🚀 Follow-Up: Optimal Approach

The most optimal way in terms of time and space is to use Binet’s Formula (closed-form expression), though due to floating point precision it may not always be accurate for large `n`.

```java
class Solution {
    public int fib(int n) {
        double phi = (1 + Math.sqrt(5)) / 2;
        return (int)Math.round(Math.pow(phi, n) / Math.sqrt(5));
    }
}
```

<div align="center">

**Time Complexity:** `O(1)` | **Space Complexity:** `O(1)`

</div>

---

## 🏆 Comparison of Approaches

| Approach                       | Time       | Space      | Pros                                  | Cons                                 |
|-------------------------------|------------|------------|---------------------------------------|--------------------------------------|
| Iterative DP                  | `O(n)`     | `O(1)`     | Simple and efficient                  | Not the fastest for `n=30` or more   |
| Recursive Memoization (Python)| `O(n)`     | `O(n)`     | Clean recursion, avoids recomputation | Uses stack memory                    |
| Binet’s Formula (Java)        | `O(1)`     | `O(1)`     | Fastest solution                      | Might have precision issues          |

---

## 🧪 Test Cases (Java)

```java
public class TestFibonacci {
    public static void main(String[] args) {
        Solution s = new Solution();
        System.out.println(s.fib(0));   // 0
        System.out.println(s.fib(1));   // 1
        System.out.println(s.fib(2));   // 1
        System.out.println(s.fib(3));   // 2
        System.out.println(s.fib(4));   // 3
        System.out.println(s.fib(10));  // 55
    }
}
```

---

<div align="center">

`Math` • `Dynamic Programming` • `Memoization` • `Recursion` • `Closed-form Formula`

---

*Happy Coding! 🚀*

</div>
