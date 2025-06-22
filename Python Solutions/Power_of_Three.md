
<div align="center">

<h1>Power of Three</h1>

</div>

---

## 📝 Problem Statement

Given an integer `n`, return `true` if it is a power of three. Otherwise, return `false`.  

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
<td><code>true</code></td>
<td><code>3^3 = 27</code></td>
</tr>
<tr>
<td><strong>2</strong></td>
<td><code>n = 0</code></td>
<td><code>false</code></td>
<td>No power of 3 is 0</td>
</tr>
<tr>
<td><strong>3</strong></td>
<td><code>n = -1</code></td>
<td><code>false</code></td>
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

Check if the number is divisible by 3 until it becomes 1. If not divisible at any step, return false.

```java
class Solution {
    public boolean isPowerOfThree(int n) {
        if (n < 1) return false;

        while (n % 3 == 0) {
            n /= 3;
        }

        return n == 1;
    }
}
```

#### 📊 Algorithm Steps

1. If `n < 1`, return `false`
2. While `n` is divisible by 3, divide it by 3
3. Return `true` if `n` becomes 1

<div align="center">

**Time Complexity:** `O(log₃ n)` | **Space Complexity:** `O(1)`

</div>

---

### Approach 2: Without Loops / Recursion (Math-Based)

Find the **maximum power of 3** that fits in a 32-bit signed integer, which is `3^19 = 1162261467`.  
If `n` is a power of 3, it must divide this number exactly.

```java
class Solution {
    public boolean isPowerOfThree(int n) {
        return n > 0 && 1162261467 % n == 0;
    }
}
```

#### 🔢 Key Insight

If `n` is a power of 3, then `1162261467 % n == 0` because 3^19 is the largest power of 3 within 32-bit range.

<div align="center">

**Time Complexity:** `O(1)` | **Space Complexity:** `O(1)`

</div>

---

## 🏆 Comparison

| Approach              | Time     | Space   | Pros                          | Cons                           |
|-----------------------|----------|---------|-------------------------------|--------------------------------|
| Iterative Division    | O(log n) | O(1)    | Simple and readable           | Slightly slower than constant |
| No Loops (Math)       | O(1)     | O(1)    | Fastest approach              | May seem like a trick solution |

---

## 🧪 Test Cases

```java
public class TestPowerOfThree {
    public static void main(String[] args) {
        Solution sol = new Solution();
        System.out.println(sol.isPowerOfThree(27));  // true
        System.out.println(sol.isPowerOfThree(0));   // false
        System.out.println(sol.isPowerOfThree(-1));  // false
        System.out.println(sol.isPowerOfThree(1));   // true (3^0)
        System.out.println(sol.isPowerOfThree(9));   // true
    }
}
```

---

<div align="center">

<code>Math</code> • <code>Loop</code> • <code>Recursion</code> • <code>Modulo</code> • <code>Easy</code>

---

*Happy Coding! 🚀*

</div>
