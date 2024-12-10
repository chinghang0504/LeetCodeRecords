# [LeetCode Records](../../README.md) - Question 1016 Binary String With Substrings Representing 1 To N

### Attempt 1: Use contains() to test every case
```java
class Solution {
    public boolean queryString(String s, int n) {
        for (int i = 1; i <= n; i++) {
            String targetStr = Integer.toBinaryString(i);
            if (!s.contains(targetStr)) {
                return false;
            }
        }

        return true;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 41.14 MB (Beats: 78.01%)

<br>
