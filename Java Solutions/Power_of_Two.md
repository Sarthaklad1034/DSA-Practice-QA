<div align="center">

<h1>Power of Two</h1>
 
</div>

---

## 📝 Problem Statement

Given an integer `n`, return `true` if it is a power of two. Otherwise, return `false`. 

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
<td><code>true</code></td>
<td><code>2^0 = 1</code></td>
</tr>
<tr>
<td><strong>2</strong></td>
<td><code>n = 16</code></td>
<td><code>true</code></td>
<td><code>2^4 = 16</code></td>
</tr>
<tr>
<td><strong>3</strong></td>
<td><code>n = 3</code></td>
<td><code>false</code></td>
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

The approach involves checking if the given integer `n` can be continuously divided by 2 until it becomes 1. If at any point `n` is not divisible by 2, it means `n` is not a power of two.

```java
class Solution {
    public boolean isPowerOfTwo(int n) {
        if (n <= 0) return false;
        
        while (n % 2 == 0) {
            n /= 2;
        }
        
        return n == 1;
    }
}
```

#### 📊 Algorithm Steps

1. **Initial Check**: If `n` is less than or equal to 0, return `false`
2. **Division Loop**: While `n` is divisible by 2, divide `n` by 2
3. **Final Check**: If the result is 1, then `n` was a power of two

<div align="center">

**Time Complexity:** `O(log n)` | **Space Complexity:** `O(1)`

</div>

---

### Approach 2: Bit Manipulation (Optimal)

A power of two in binary representation has exactly one bit set to 1. We can use the property that `n & (n-1)` equals 0 for powers of two.

```java
class Solution {
    public boolean isPowerOfTwo(int n) {
        return n > 0 && (n & (n - 1)) == 0;
    }
}
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
- `n` has exactly one bit set to 1
- `n-1` has all bits set to 1 up to the position where `n` has its single 1 bit
- `n & (n-1)` results in 0

<div align="center">

**Time Complexity:** `O(1)` | **Space Complexity:** `O(1)`

</div>

---

## 🏆 Comparison

| Approach | Time | Space | Pros | Cons |
|----------|------|-------|------|------|
| **Iterative** | O(log n) | O(1) | Easy to understand | Slower for large numbers |
| **Bit Manipulation** | O(1) | O(1) | Constant time, elegant | Requires bit manipulation knowledge |

---

## 🧪 Test Cases

```java
// Test the solution
public class TestPowerOfTwo {
    public static void main(String[] args) {
        Solution solution = new Solution();
        
        // Test cases
        System.out.println(solution.isPowerOfTwo(1));    // true
        System.out.println(solution.isPowerOfTwo(16));   // true  
        System.out.println(solution.isPowerOfTwo(3));    // false
        System.out.println(solution.isPowerOfTwo(0));    // false
        System.out.println(solution.isPowerOfTwo(-16));  // false
    }
}
```

---

<div align="center">

`Math` • `Bit Manipulation` • `Binary Operations` • `Easy` • `Recursion`

---

*Happy Coding! 🚀*

</div>