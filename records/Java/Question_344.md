# [LeetCode Records](../../README.md) - Question 344 Reverse String

### Attempt 1: 
```java
class Solution {
    public void reverseString(char[] s) {
        for (int i = 0; i < s.length / 2; i++) {
            char ch = s[i];
            s[i] = s[s.length - 1 - i];
            s[s.length - i - 1] = ch;
        }
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 48.88 MB (Beats: 62.25%)

<br>
