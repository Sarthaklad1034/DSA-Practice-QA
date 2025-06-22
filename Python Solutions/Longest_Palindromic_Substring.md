
<div align="center">

# 🔠 Longest Palindromic Substring

</div>

---

## 📝 Problem Statement

Given a string `s`, return the **longest palindromic substring** in `s`.

---

## 🔍 Examples

| Example | Input              | Output  | Explanation                                    |
|---------|-------------------|---------|------------------------------------------------|
| 1       | `s = "babad"`      | `"bab"` or `"aba"` | Both are valid palindromic substrings |
| 2       | `s = "cbbd"`       | `"bb"`  | "bb" is the longest palindromic substring      |
| 3       | `s = "a"`          | `"a"`   | Single character string is a palindrome        |

---

## ⚙️ Constraints

- `1 <= s.length <= 1000`
- `s` consists of only digits and English letters.

---

## 🛠️ Solution Approaches

### ✅ Approach 1: Expand Around Center (Java)

Expand from each character and pair of characters to find all palindromes.

```java
class Solution {
    public String longestPalindrome(String s) {
        if (s ==  null || s.length() < 1) return "";

        int start = 0, end = 0;
        char[] c = s.toCharArray();

        for (int i = 0; i < s.length(); i++) {
            int len1 = isPalidrome(i , i, c);
            int len2 = isPalidrome(i, i+1, c);
            int len = Math.max(len1, len2);

            if (len > end - start) {
                start = i - (len - 1) / 2;
                end = i + len / 2;
            }
        }
        return s.substring(start, end+1);
    }

    private int isPalidrome(int s, int e, char[] c) {
        while (s >= 0 && e < c.length && c[s] == c[e]) {
            s--;
            e++;
        }
        return e - s - 1;
    }
}
```

**Time Complexity:** `O(n^2)`  
**Space Complexity:** `O(1)`

---

### 🐍 Approach 2: Expand Around Center (Python)

Simple and efficient implementation using two-pointer expansion from center.

```python
class Solution:
    def longestPalindrome(self, s: str) -> str:
        if not s or len(s) < 1:
            return ""

        start, end = 0, 0

        def expand(left, right):
            while left >= 0 and right < len(s) and s[left] == s[right]:
                left -= 1
                right += 1
            return right - left - 1

        for i in range(len(s)):
            len1 = expand(i, i)
            len2 = expand(i, i + 1)
            length = max(len1, len2)

            if length > end - start:
                start = i - (length - 1) // 2
                end = i + length // 2

        return s[start:end + 1]
```

**Time Complexity:** `O(n^2)`  
**Space Complexity:** `O(1)`

---

## 🏆 Comparison of Approaches

| Approach                    | Time Complexity | Space Complexity | Language | Description                           |
|----------------------------|------------------|-------------------|----------|---------------------------------------|
| Expand Around Center (Java)| O(n^2)           | O(1)              | Java     | Efficient and widely used technique   |
| Expand Around Center (Python)| O(n^2)         | O(1)              | Python   | Clean and compact Python version      |

---

## 🧪 Test Cases

### Java
```java
public class Main {
    public static void main(String[] args) {
        Solution sol = new Solution();
        System.out.println(sol.longestPalindrome("babad")); // bab or aba
        System.out.println(sol.longestPalindrome("cbbd"));  // bb
        System.out.println(sol.longestPalindrome("a"));     // a
    }
}
```

### Python
```python
sol = Solution()
print(sol.longestPalindrome("babad"))  # "bab" or "aba"
print(sol.longestPalindrome("cbbd"))   # "bb"
print(sol.longestPalindrome("a"))      # "a"
```

---

<div align="center">

💡 *Dynamic Programming* • *Expand Around Center* • *Two Pointers*

</div>
