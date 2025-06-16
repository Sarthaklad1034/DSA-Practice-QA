
<div align="center">

<h1>Power of Four (Python)</h1>

</div>

---

## 📝 Problem Statement

Given an integer `n`, return `True` if it is a power of four. Otherwise, return `False`.  

An integer `n` is a power of four if there exists an integer `x` such that:  
`n = 4^x`

---

## 🔍 Examples

| Example | Input      | Output | Explanation        |
|---------|------------|--------|--------------------|
| 1       | `n = 16`   | `True` | `4^2 = 16`         |
| 2       | `n = 5`    | `False`| Not a power of 4   |
| 3       | `n = 1`    | `True` | `4^0 = 1`          |

---

## ⚡ Constraints

```
-2^31 <= n <= 2^31 - 1
```

---

## 🛠️ Solution Approaches

### ✅ Approach 1: Iterative Division (Given)

```python
class Solution(object):
    def isPowerOfFour(self, n):
        if n < 1:
            return False
        while n > 1:
            if n % 4 != 0:
                return False
            n /= 4
        return n == 1
```

#### 📊 Algorithm Steps

1. If `n < 1`, return `False`
2. While `n` is divisible by 4, divide it by 4
3. Return `True` if `n` becomes 1

<div align="center">

**Time Complexity:** `O(log₄ n)` | **Space Complexity:** `O(1)`

</div>

---

### 🔁 Approach 2: Bit Manipulation (Follow-up)

Check two things:
- `n` is a power of two (only one bit set)
- The 1-bit is in an even position (characteristic of power of 4)

```python
class Solution(object):
    def isPowerOfFour(self, n):
        return n > 0 and (n & (n - 1)) == 0 and (n & 0xAAAAAAAA) == 0
```

#### 🔢 Explanation

- `(n & (n - 1)) == 0`: Ensures only one bit is set (power of 2)
- `0xAAAAAAAA`: Mask with 1s at odd positions to exclude powers of 2 that aren't also powers of 4

<div align="center">

**Time Complexity:** `O(1)` | **Space Complexity:** `O(1)`

</div>

---

## 🧪 Test Cases

```python
sol = Solution()
print(sol.isPowerOfFour(16))  # True
print(sol.isPowerOfFour(5))   # False
print(sol.isPowerOfFour(1))   # True
print(sol.isPowerOfFour(0))   # False
print(sol.isPowerOfFour(64))  # True
```

---

<div align="center">

<code>Math</code> • <code>Bit Manipulation</code> • <code>Loop</code> • <code>Recursion</code> • <code>Python</code>

---

*Happy Coding! 🚀*

</div>
