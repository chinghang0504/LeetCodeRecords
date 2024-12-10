# [LeetCode Records](../../README.md) - Question 1003 Check If Word Is Valid After Substitutions

### Attempt 1: Use replace() to remove "abc" strings
```java
class Solution {
    public boolean isValid(String s) {
        int len = s.length();
        if (len % 3 != 0) {
            return false;
        }

        int prevLen;
        do {
            prevLen = len;
            s = s.replace("abc", "");
            len = s.length();
        } while (prevLen != len);

        return s.length() == 0;
    }
}
```
- Runtime: 4 ms (Beats: 96.98%)
- Memory: 43.98 MB (Beats: 99.70%)

<br>
