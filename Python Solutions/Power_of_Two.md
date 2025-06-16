<div align="center">

<h1>Power of Two</h1>

</div>

---

## 📝 Problem Statement

Given an integer `n`, return `True` if it is a power of two. Otherwise, return `False`. 

An integer `n` is a power of two if there exists an integer `x` such that `n = 2^x`.

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
<td><code>n = 1</code></td>
<td><code>True</code></td>
<td><code>2^0 = 1</code></td>
</tr>
<tr>
<td><strong>2</strong></td>
<td><code>n = 16</code></td>
<td><code>True</code></td>
<td><code>2^4 = 16</code></td>
</tr>
<tr>
<td><strong>3</strong></td>
<td><code>n = 3</code></td>
<td><code>False</code></td>
<td>Cannot be expressed as <code>2^x</code></td>
</tr>
</table>

## ⚡ Constraints

```
-2^31 <= n <= 2^31 - 1
```

---

## 🛠️ Solution Approaches

### Approach 1: Iterative Division

This approach checks if the given integer `n` can be continuously divided by 2 until it becomes 1. If at any point `n` is not divisible by 2, it means `n` is not a power of two.

```python
class Solution(object):
    def isPowerOfTwo(self, n):
        if n == 0:
            return False
        while n % 2 == 0:
            n /= 2
        return n == 1
```

#### 📊 Algorithm Steps

1. **Initial Check**: If `n` is 0, return `False`
2. **Loop**: While `n` is divisible by 2, divide `n` by 2
3. **Final Check**: If the result is 1, return `True`, else `False`

<div align="center">

**Time Complexity:** `O(log n)` | **Space Complexity:** `O(1)`

</div>

---

### Approach 2: Bit Manipulation (Optimal)

A power of two has exactly one bit set in binary. So, `n & (n-1) == 0` only for powers of two.

```python
class Solution(object):
    def isPowerOfTwo(self, n):
        return n > 0 and (n & (n - 1)) == 0
```

#### 🔢 Binary Analysis

<table>
<tr>
<th>Number</th>
<th>Binary</th>
<th>n-1 Binary</th>
<th>n & (n-1)</th>
<th>Power of 2?</th>
</tr>
<tr>
<td>1</td>
<td><code>0001</code></td>
<td><code>0000</code></td>
<td><code>0000</code></td>
<td>✅ Yes</td>
</tr>
<tr>
<td>2</td>
<td><code>0010</code></td>
<td><code>0001</code></td>
<td><code>0000</code></td>
<td>✅ Yes</td>
</tr>
<tr>
<td>4</td>
<td><code>0100</code></td>
<td><code>0011</code></td>
<td><code>0000</code></td>
<td>✅ Yes</td>
</tr>
<tr>
<td>5</td>
<td><code>0101</code></td>
<td><code>0100</code></td>
<td><code>0100</code></td>
<td>❌ No</td>
</tr>
</table>

#### 💡 Key Insight

For any power of two `n`:
- It has only one set bit
- `n-1` flips all lower bits
- `n & (n-1)` becomes 0

<div align="center">

**Time Complexity:** `O(1)` | **Space Complexity:** `O(1)`

</div>

---

## 🏆 Comparison

| Approach | Time | Space | Pros | Cons |
|----------|------|-------|------|------|
| **Iterative** | O(log n) | O(1) | Simple logic | Slower |
| **Bit Manipulation** | O(1) | O(1) | Efficient and clean | Bitwise logic might be tricky |

---

## 🧪 Test Cases

```python
def test():
    s = Solution()
    print(s.isPowerOfTwo(1))    # True
    print(s.isPowerOfTwo(16))   # True  
    print(s.isPowerOfTwo(3))    # False
    print(s.isPowerOfTwo(0))    # False
    print(s.isPowerOfTwo(-16))  # False

test()
```

---

<div align="center">

`Math` • `Bit Manipulation` • `Binary Operations` • `Easy` • `Recursion`

---

*Happy Coding! 🚀*

</div>