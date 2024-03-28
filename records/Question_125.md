# [LeetCode Records](../README.md) - Question 125 Valid Palindrome

### Attempt 1: Convert the entire string and then check the string
```java
class Solution {
    public boolean isPalindrome(String s) {
        s = s.replaceAll("[^A-Za-z0-9]", "");
        s = s.toLowerCase();

        int size = s.length();
        for (int i = 0; i < size / 2; i++) {
            if (s.charAt(i) != s.charAt(size - i - 1)) {
                return false;
            }
        }

        return true;
    }
}
```
- Runtime: 14 ms (Beats: 37.52%)
- Memory: 44.35 MB (Beats: 46.48%)

<br>

### Attempt 2: Check from the begin and the end character first
```java
class Solution {
    public boolean isPalindrome(String s) {
        int i = 0;
        int j = s.length() - 1;

        while (i < j) {
            char ch1 = s.charAt(i);
            if (!isValidCharacter(ch1)) {
                i++;
                continue;
            }

            char ch2 = s.charAt(j);
            if (!isValidCharacter(ch2)) {
                j--;
                continue;
            }

            if (ch1 != ch2 && Character.toLowerCase(ch1) != Character.toLowerCase(ch2)) {
                return false;
            }

            i++;
            j--;
        }

        return true;
    }

    public boolean isValidCharacter(char ch) {
        return (ch >= 'A' && ch <= 'Z' || ch >= 'a' && ch <= 'z' || ch >= '0' && ch <= '9');
    }
}
```
- Runtime: 1 ms (Beats: 100.00%)
- Memory: 42.86 MB (Beats: 73.82%)

<br>
