
<div align="center">

# 🔢 9. Palindrome Number

</div>

---

## 📝 Problem Statement

Given an integer `x`, return `true` if `x` is a **palindrome**, and `false` otherwise.

---

## 🔍 Examples

| Example | Input    | Output | Explanation                                                                 |
|---------|----------|--------|-----------------------------------------------------------------------------|
| 1       | `x = 121`| `true` | 121 reads the same from left to right and right to left.                    |
| 2       | `x = -121`| `false`| From left to right: `-121`, from right to left: `121-`. Not a palindrome.   |
| 3       | `x = 10` | `false`| Reads as `01` in reverse. Not a palindrome.                                |

---

## ⚙️ Constraints

- `-2^31 <= x <= 2^31 - 1`

---

## 🛠️ Solution Approaches

### ✅ Approach 1: Reversing the Number (Java)

Check if the reversed number equals the original. Skip negative numbers immediately.

```java
class Solution {
    public boolean isPalindrome(int x) {
        if (x < 0) return false;
        int original = x;
        int rev = 0;
        while (x > 0) {
            rev = rev * 10 + x % 10;  
            x /= 10;                 
        }
        return rev == original;
    }
}
```

**Time Complexity:** `O(log₁₀ n)`  
**Space Complexity:** `O(1)`

---

### 🐍 Approach 2: Reversing the Number (Python)

Same approach as above, written in Python for simplicity.

```python
class Solution(object):
    def isPalindrome(self, x):
        if x < 0:
            return False
        num = x
        rev = 0

        while num > 0:
            rev = rev * 10 + num % 10
            num //= 10

        return rev == x
```

**Time Complexity:** `O(log₁₀ n)`  
**Space Complexity:** `O(1)`

---

## 🏆 Comparison of Approaches

| Approach                     | Time Complexity | Space Complexity | Language | Description                      |
|-----------------------------|------------------|-------------------|----------|----------------------------------|
| Reverse Integer (Java)      | O(log₁₀ n)       | O(1)              | Java     | Standard approach, precise       |
| Reverse Integer (Python)    | O(log₁₀ n)       | O(1)              | Python   | Clean and intuitive              |

---

## 🧪 Test Cases

### Java
```java
public class Main {
    public static void main(String[] args) {
        Solution sol = new Solution();
        System.out.println(sol.isPalindrome(121));  // true
        System.out.println(sol.isPalindrome(-121)); // false
        System.out.println(sol.isPalindrome(10));   // false
    }
}
```

### Python
```python
sol = Solution()
print(sol.isPalindrome(121))   # True
print(sol.isPalindrome(-121))  # False
print(sol.isPalindrome(10))    # False
```

---

<div align="center">

💡 *Math* • *Integer Manipulation*

</div>
