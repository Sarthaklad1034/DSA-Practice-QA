
<div align="center">

<h1>Palindromic Substrings</h1>

</div>

---

## 📝 Problem Statement

Given a string `s`, return the **number of palindromic substrings** in it.

A string is a **palindrome** when it reads the same backward as forward.

A **substring** is a contiguous sequence of characters within the string.

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
<td><code>s = "abc"</code></td>
<td><code>3</code></td>
<td><code>"a", "b", "c"</code> are all palindromic substrings.</td>
</tr>
<tr>
<td><strong>2</strong></td>
<td><code>s = "aaa"</code></td>
<td><code>6</code></td>
<td><code>"a", "a", "a", "aa", "aa", "aaa"</code> are palindromic substrings.</td>
</tr>
</table>

---

## ⚡ Constraints

```
1 <= s.length <= 1000
s consists of lowercase English letters.
```

---

## 🛠️ Solution Approaches

### ✅ Approach 1: Expand Around Center (Java)

Expand around every possible center and count palindromes dynamically.

```java
class Solution {
    public int countSubstrings(String s) {
        if (s.length() == 0) return 0;
        int n = s.length();
        int res = 0;
        char[] c = s.toCharArray();

        for (int i = 0; i < n; i++) {
            res += isPalidrome(i, i, c);
            res += isPalidrome(i, i + 1, c);
        }
        return res;
    }

    public int isPalidrome(int s, int e, char[] c) {
        int count = 0;
        while (s >= 0 && e < c.length && c[s--] == c[e++]) count++;
        return count;
    }
}
```

<div align="center">

**Time Complexity:** `O(n^2)` | **Space Complexity:** `O(1)`

</div>

---

### ✅ Approach 2: Expand Around Center (Python)

Same logic using Python with clean function definition and readability.

```python
class Solution:
    def countSubstrings(self, s: str) -> int:
        def expandAroundCenter(left: int, right: int) -> int:
            count = 0
            while left >= 0 and right < len(s) and s[left] == s[right]:
                count += 1
                left -= 1
                right += 1
            return count

        res = 0
        for i in range(len(s)):
            res += expandAroundCenter(i, i)
            res += expandAroundCenter(i, i + 1)
        return res
```

<div align="center">

**Time Complexity:** `O(n^2)` | **Space Complexity:** `O(1)`

</div>

---

## 🏆 Comparison of Approaches

| Approach                      | Time       | Space      | Pros                        | Cons              |
|------------------------------|------------|------------|-----------------------------|-------------------|
| Expand Around Center (Java)  | `O(n^2)`   | `O(1)`     | Simple and fast for `n<=1k` | Not fastest for huge `n` |
| Expand Around Center (Python)| `O(n^2)`   | `O(1)`     | Pythonic, clean logic       | Same as above     |

---

## 🧪 Test Cases

```java
public class Main {
    public static void main(String[] args) {
        Solution sol = new Solution();
        System.out.println(sol.countSubstrings("abc")); // 3
        System.out.println(sol.countSubstrings("aaa")); // 6
    }
}
```

```python
sol = Solution()
print(sol.countSubstrings("abc"))  # 3
print(sol.countSubstrings("aaa"))  # 6
```

---

<div align="center">

`Two Pointers` • `String Manipulation` • `Dynamic Counting`

---

*Happy Coding! 🚀*

</div>
