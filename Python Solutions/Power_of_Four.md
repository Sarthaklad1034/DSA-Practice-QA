
<div align="center">

<h1>Power of Four</h1>

</div>

---

## 📝 Problem Statement

Given an integer `n`, return `true` if it is a power of four. Otherwise, return `false`.  

An integer `n` is a power of four if there exists an integer `x` such that:  
`n = 4^x`

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
<td><code>n = 16</code></td>
<td><code>true</code></td>
<td><code>4^2 = 16</code></td>
</tr>
<tr>
<td><strong>2</strong></td>
<td><code>n = 5</code></td>
<td><code>false</code></td>
<td>Cannot be expressed as <code>4^x</code></td>
</tr>
<tr>
<td><strong>3</strong></td>
<td><code>n = 1</code></td>
<td><code>true</code></td>
<td><code>4^0 = 1</code></td>
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

Check if the number is divisible by 4 until it becomes 1. If not divisible at any step, return false.

```java
class Solution {
    public boolean isPowerOfFour(int n) {
        if (n < 1) return false;

        while (n % 4 == 0) {
            n /= 4;
        }

        return n == 1;
    }
}
```

#### 📊 Algorithm Steps

1. If `n < 1`, return `false`
2. While `n` is divisible by 4, divide it by 4
3. Return `true` if `n` becomes 1

<div align="center">

**Time Complexity:** `O(log₄ n)` | **Space Complexity:** `O(1)`

</div>

---

### Approach 2: Without Loops / Recursion (Bit Manipulation)

Check if:
- `n` is a power of two (only one bit set)
- AND that bit is at the **even position** (power of 4)

```java
class Solution {
    public boolean isPowerOfFour(int n) {
        return n > 0 && (n & (n - 1)) == 0 && (n & 0xAAAAAAAA) == 0;
    }
}
```

#### 🔢 Key Insight

- `(n & (n - 1)) == 0` checks if it's a power of 2
- `(n & 0xAAAAAAAA) == 0` ensures the 1-bit is in an **even position**

<div align="center">

**Time Complexity:** `O(1)` | **Space Complexity:** `O(1)`

</div>

---

## 🏆 Comparison

| Approach              | Time     | Space   | Pros                          | Cons                           |
|-----------------------|----------|---------|-------------------------------|--------------------------------|
| Iterative Division    | O(log n) | O(1)    | Easy to implement             | Slower, uses loop             |
| Bit Manipulation      | O(1)     | O(1)    | Fast and loop-free            | Less intuitive                |

---

## 🧪 Test Cases

```java
public class TestPowerOfFour {
    public static void main(String[] args) {
        Solution sol = new Solution();
        System.out.println(sol.isPowerOfFour(16));  // true
        System.out.println(sol.isPowerOfFour(5));   // false
        System.out.println(sol.isPowerOfFour(1));   // true
        System.out.println(sol.isPowerOfFour(0));   // false
        System.out.println(sol.isPowerOfFour(64));  // true
    }
}
```

---

<div align="center">

<code>Math</code> • <code>Bit Manipulation</code> • <code>Loop</code> • <code>Recursion</code> • <code>Easy</code>

---

*Happy Coding! 🚀*

</div>
