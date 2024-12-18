# [LeetCode Records](../../README.md) - Question 3084 Count Substrings Starting and Ending with Given Character

### Attempt 1: Use the sum of integers formula
```java
class Solution {
    public long countSubstrings(String s, char c) {
        int count = 0;
        for (int i = 0; i < s.length(); i++) {
            if (s.charAt(i) == c) {
                count++;
            }
        }

        return (long)count * (1 + count) / 2;
    }
}
```
- Runtime: 1 ms (Beats: 100.00%)
- Memory: 45.22 MB (Beats: 7.85%)

<br>
