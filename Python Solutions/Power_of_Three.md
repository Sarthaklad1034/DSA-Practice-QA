<div align="center">

<h1>Power of Three</h1>

</div>

---

## 📝 Problem Statement

Given an integer `n`, return `True` if it is a power of three. Otherwise, return `False`.  

An integer `n` is a power of three if there exists an integer `x` such that:  
`n = 3^x`

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
<td><code>n = 27</code></td>
<td><code>True</code></td>
<td><code>3^3 = 27</code></td>
</tr>
<tr>
<td><strong>2</strong></td>
<td><code>n = 0</code></td>
<td><code>False</code></td>
<td>No power of 3 is 0</td>
</tr>
<tr>
<td><strong>3</strong></td>
<td><code>n = -1</code></td>
<td><code>False</code></td>
<td>Negative numbers can't be powers of 3</td>
</tr>
</table>

---

## ⚡ Constraints

```
-2^31 <= n <= 2^31 - 1
```

---

## 🛠️ Solution Approaches

### Approach 1: Iterative Division

Repeatedly divide the number by 3. If at any step the number is not divisible by 3, return `False`.

```python
class Solution(object):
    def isPowerOfThree(self, n):
        if n < 1:
            return False
        while n > 1:
            if n % 3 != 0:
                return False
            n /= 3
        return n == 1
```

#### 📊 Algorithm Steps

1. If `n < 1`, return `False`
2. While `n > 1`, check if divisible by 3
3. If not divisible, return `False`; otherwise, divide it by 3
4. At the end, check if `n` equals 1

<div align="center">

**Time Complexity:** `O(log₃ n)` | **Space Complexity:** `O(1)`

</div>

---

### Approach 2: Math-based Optimization (No Loops or Recursion)

Find the largest power of 3 within 32-bit integer range: `3^19 = 1162261467`.  
If `n` divides this exactly, then it's a power of 3.

```python
class Solution(object):
    def isPowerOfThree(self, n):
        return n > 0 and 1162261467 % n == 0
```

#### 🔢 Key Insight

- 1162261467 is the largest power of 3 within 32-bit signed integer.
- All lower powers of 3 divide it exactly.

<div align="center">

**Time Complexity:** `O(1)` | **Space Complexity:** `O(1)`

</div>

---

## 🏆 Comparison

| Approach              | Time     | Space   | Pros                          | Cons                           |
|-----------------------|----------|---------|-------------------------------|--------------------------------|
| Iterative Division    | O(log n) | O(1)    | Simple and readable           | Slightly slower                |
| No Loops (Math)       | O(1)     | O(1)    | Fast and efficient            | Requires known constant        |

---

## 🧪 Test Cases

```python
def test():
    s = Solution()
    print(s.isPowerOfThree(27))   # True
    print(s.isPowerOfThree(0))    # False
    print(s.isPowerOfThree(-1))   # False
    print(s.isPowerOfThree(1))    # True
    print(s.isPowerOfThree(9))    # True

test()
```

---

<div align="center">

<code>Math</code> • <code>Loop</code> • <code>Recursion</code> • <code>Modulo</code> • <code>Easy</code>

---

*Happy Coding! 🚀*

</div>