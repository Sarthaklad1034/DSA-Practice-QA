
<div align="center">

# Longest Palindrome

</div>

---

## 📝 Problem Statement

Given a string `s` which consists of lowercase or uppercase letters, return the length of the **longest palindrome** that can be built with those letters.

**Note:** Letters are **case sensitive**, for example, `"Aa"` is not considered a palindrome.

---

## 🔍 Examples

| Example | Input           | Output | Explanation                                                              |
|---------|------------------|--------|--------------------------------------------------------------------------|
| 1       | `s = "abccccdd"` | `7`    | One longest palindrome that can be built is `"dccaccd"`, length is 7.    |
| 2       | `s = "a"`        | `1`    | The longest palindrome that can be built is `"a"`, length is 1.          |

---

## ⚙️ Constraints

- `1 <= s.length <= 2000`
- `s` consists of lowercase and/or uppercase English letters only.

---

## 🛠️ Solution Approaches

### ✅ Approach 1: Set Based Character Count (Java)

Use an array to keep track of characters that have been seen an odd number of times. Every time a character completes a pair, increase the result by 2.

```java
class Solution {
    public int longestPalindrome(String s) {
        int set[] = new int[128];
        int res = 0;
        int oddCount = 0;
        for (char ch : s.toCharArray()) {
            if (set[ch] != 0) {
                res += 2;
                set[ch] = 0;
                oddCount--;
            } else {
                set[ch] = 1;
                oddCount++;
            }
        }
        if (oddCount > 0) {
            res += 1;
        }
        return res;
    }
}
```

**Time Complexity:** `O(n)`  
**Space Complexity:** `O(1)`

---

### 🔁 Approach 2: Optimized Frequency Map (Java)

Count frequencies, sum all even pairs, and add `+1` if any character has an odd count.

```java
import java.util.HashMap;

class Solution {
    public int longestPalindrome(String s) {
        HashMap<Character, Integer> freq = new HashMap<>();
        for (char c : s.toCharArray()) {
            freq.put(c, freq.getOrDefault(c, 0) + 1);
        }

        int length = 0;
        boolean oddFound = false;

        for (int count : freq.values()) {
            length += count / 2 * 2;
            if (count % 2 == 1) oddFound = true;
        }

        return oddFound ? length + 1 : length;
    }
}
```

**Time Complexity:** `O(n)`  
**Space Complexity:** `O(k)` where `k` is the number of unique characters

---

### 🐍 Approach 3: Optimized Counter Based (Python)

Pythonic and simple using collections.Counter.

```python
from collections import Counter

class Solution:
    def longestPalindrome(self, s: str) -> int:
        counts = Counter(s)
        length = 0
        odd_found = False

        for count in counts.values():
            length += count // 2 * 2
            if count % 2 == 1:
                odd_found = True

        return length + 1 if odd_found else length
```

**Time Complexity:** `O(n)`  
**Space Complexity:** `O(k)`

---

## 🏆 Comparison of Approaches

| Approach                             | Time Complexity | Space Complexity | Language | Description                         |
|-------------------------------------|------------------|-------------------|----------|-------------------------------------|
| Character Set (Java)                | O(n)             | O(1)              | Java     | Fast and minimal space              |
| HashMap Frequency Count (Java)      | O(n)             | O(k)              | Java     | Slightly more readable and flexible |
| Counter Based Solution (Python)     | O(n)             | O(k)              | Python   | Most elegant in Python              |

---

## 🧪 Test Cases

### Java
```java
public class Main {
    public static void main(String[] args) {
        Solution sol = new Solution();
        System.out.println(sol.longestPalindrome("abccccdd")); // 7
        System.out.println(sol.longestPalindrome("a"));        // 1
        System.out.println(sol.longestPalindrome("Aa"));       // 1
    }
}
```

### Python
```python
sol = Solution()
print(sol.longestPalindrome("abccccdd"))  # 7
print(sol.longestPalindrome("a"))         # 1
print(sol.longestPalindrome("Aa"))        # 1
```

---

<div align="center">

💡 *Greedy* • *Hash Table* • *String*

</div>
