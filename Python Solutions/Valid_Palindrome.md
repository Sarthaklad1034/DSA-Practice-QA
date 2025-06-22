
<div align="center">

<h1>Valid Palindrome</h1>

</div>

---

## 📝 Problem Statement

A phrase is a **palindrome** if, after converting all uppercase letters into lowercase letters and removing all non-alphanumeric characters, it reads the same forward and backward.

Alphanumeric characters include letters and numbers.

Given a string `s`, return `true` *if it is a palindrome*, or `false` otherwise.

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
<td><code>s = "A man, a plan, a canal: Panama"</code></td>
<td><code>true</code></td>
<td><code>"amanaplanacanalpanama"</code> is a palindrome.</td>
</tr>
<tr>
<td><strong>2</strong></td>
<td><code>s = "race a car"</code></td>
<td><code>false</code></td>
<td><code>"raceacar"</code> is not a palindrome.</td>
</tr>
<tr>
<td><strong>3</strong></td>
<td><code>s = " "</code></td>
<td><code>true</code></td>
<td>Empty string after cleanup is a palindrome.</td>
</tr>
</table>

---

## ⚙️ Constraints

- `1 <= s.length <= 2 * 10^5`
- `s` consists only of printable ASCII characters.

---

## 🛠️ Solution Approaches

### ✅ Approach 1: Basic Two Pointer with Cleanup (Java)

This solution first converts the string to lowercase and removes all non-alphanumeric characters using regex. Then, two pointers are used to check whether the string is a palindrome.

```java
class Solution {
    public boolean isPalindrome(String s) {
        s = s.toLowerCase().replaceAll("[^A-Za-z0-9]", "");
        int i = 0;
        int j = s.length() - 1;
        while (i <= j) {
            if (s.charAt(i) != s.charAt(j)) return false;
            i++;
            j--;
        }
        return true;
    }
}
```

**Time Complexity:** `O(n)`  
**Space Complexity:** `O(n)` (due to string replacement and lowercase conversion)

---

### 🔁 Approach 2: Optimized Two Pointer (Java)

Avoids creating a new string. Instead, directly compares characters by skipping non-alphanumerics using character checks.

```java
class Solution {
    public boolean isPalindrome(String s) {
        int i = 0, j = s.length() - 1;
        while (i < j) {
            while (i < j && !Character.isLetterOrDigit(s.charAt(i))) i++;
            while (i < j && !Character.isLetterOrDigit(s.charAt(j))) j--;
            if (Character.toLowerCase(s.charAt(i)) != Character.toLowerCase(s.charAt(j)))
                return false;
            i++;
            j--;
        }
        return true;
    }
}
```

**Time Complexity:** `O(n)`  
**Space Complexity:** `O(1)`

---

### 🐍 Approach 3: Regex Cleanup and Two Pointer (Python)

Uses Python's `re` module to clean the string and then applies a similar two-pointer logic.

```python
import re

class Solution:
    def isPalindrome(self, s: str) -> bool:
        s = re.sub(r'[^A-Za-z0-9]', '', s).lower()
        i = 0
        j = len(s) - 1
        while i <= j:
            if s[i] != s[j]:
                return False
            i += 1
            j -= 1
        return True
```

**Time Complexity:** `O(n)`  
**Space Complexity:** `O(n)`

---

## 🏆 Comparison of Approaches

| Approach                          | Time Complexity | Space Complexity | Pros                            | Cons                         |
|----------------------------------|------------------|-------------------|----------------------------------|------------------------------|
| Basic Two Pointer (Java)         | O(n)             | O(n)              | Simple and easy to understand    | Extra space due to cleanup   |
| Optimized Two Pointer (Java)     | O(n)             | O(1)              | Most space-efficient             | Slightly more complex logic  |
| Regex & Two Pointer (Python)     | O(n)             | O(n)              | Readable and concise in Python   | Uses extra space             |

---

## 🧪 Test Cases

### Java
```java
public class Main {
    public static void main(String[] args) {
        Solution sol = new Solution();
        System.out.println(sol.isPalindrome("A man, a plan, a canal: Panama")); // true
        System.out.println(sol.isPalindrome("race a car")); // false
        System.out.println(sol.isPalindrome("")); // true
    }
}
```

### Python
```python
sol = Solution()
print(sol.isPalindrome("A man, a plan, a canal: Panama"))  # True
print(sol.isPalindrome("race a car"))  # False
print(sol.isPalindrome(""))  # True
```

---

<div align="center">

💡 *String Manipulation* • *Two Pointers* • *Regex*

</div>
