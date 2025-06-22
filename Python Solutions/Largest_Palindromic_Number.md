
<div align="center">

<h1>2384. Largest Palindromic Number</h1>

</div>

---

## 📝 Problem Statement

You are given a string `num` consisting of digits only.

Return the **largest palindromic** integer (in the form of a string) that can be formed using digits taken from `num`. It should not contain **leading zeroes**.

---

### 🔎 Notes

- You do **not** need to use all the digits of `num`, but you must use **at least one** digit.
- The digits can be **reordered**.

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
<td><code>num = "444947137"</code></td>
<td><code>"7449447"</code></td>
<td>Use digits "4449477" to form "7449447".</td>
</tr>
<tr>
<td><strong>2</strong></td>
<td><code>num = "00009"</code></td>
<td><code>"9"</code></td>
<td>Only non-zero digit "9" can form a valid palindrome without leading zeroes.</td>
</tr>
</table>

---

## ⚙️ Constraints

- `1 <= num.length <= 10^5`
- `num` consists of digits.

---

## 🛠️ Solution Approaches

### ✅ Approach 1: Greedy Digit Count & Build (Java)

We count frequency of each digit, and construct the largest possible palindrome from the outside in. The largest available odd-count digit (if any) goes in the middle.

```java
import java.util.*;

class Solution {
    public String largestPalindromic(String num) {
        int[] count = new int[10];

        // Count frequency of each digit
        for (char c : num.toCharArray()) {
            count[c - '0']++;
        }

        StringBuilder half = new StringBuilder();
        // Build half of the palindrome from largest to smallest digit
        for (int i = 9; i >= 0; i--) {
            int pairs = count[i] / 2;
            if (i != 0 || half.length() > 0) {
                while (pairs-- > 0) {
                    half.append(i);
                }
            }
        }

        // Find the max digit for the center if available
        String mid = "";
        for (int i = 9; i >= 0; i--) {
            if (count[i] % 2 == 1) {
                mid = String.valueOf(i);
                break;
            }
        }

        String halfStr = half.toString();
        String revHalf = half.reverse().toString();

        String result = halfStr + mid + revHalf;
        return result.isEmpty() ? "0" : result;
    }
}
```

**Time Complexity:** `O(n)`  
**Space Complexity:** `O(1)` (fixed array of size 10)

---

### 🐍 Approach 2: Python Greedy Using Dict and String Manipulation

We use `collections.defaultdict` to count digits and build the half string greedily from 9 to 0. The middle digit is chosen from the largest remaining odd-count digit.

```python
import collections

class Solution:
    def largestPalindromic(self, num: str) -> str:
        count = collections.defaultdict(int)
        for n in num:
            count[n] += 1
        res = ''
        for i in '9876543210':
            res += (count[i] // 2) * i
        res = res.lstrip('0')
        mid = max((count[i] % 2 * i for i in count), default='')
        return (res + mid + res[::-1]) or '0'
```

**Time Complexity:** `O(n)`  
**Space Complexity:** `O(1)`

---

## 🏆 Comparison of Approaches

| Approach                     | Time Complexity | Space Complexity | Pros                              | Cons                       |
|-----------------------------|------------------|-------------------|-----------------------------------|----------------------------|
| Greedy Count + Build (Java) | O(n)             | O(1)              | Efficient and clean, constant space | Slightly longer syntax     |
| Python Greedy Dict          | O(n)             | O(1)              | Compact and expressive            | Uses defaultdict            |

---

## 🧪 Test Cases

### Java
```java
public class Main {
    public static void main(String[] args) {
        Solution sol = new Solution();
        System.out.println(sol.largestPalindromic("444947137")); // "7449447"
        System.out.println(sol.largestPalindromic("00009")); // "9"
    }
}
```

### Python
```python
sol = Solution()
print(sol.largestPalindromic("444947137"))  # "7449447"
print(sol.largestPalindromic("00009"))  # "9"
```

---

<div align="center">

📊 *Greedy* • *Frequency Counting* • *String Manipulation*

</div>
