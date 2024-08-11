# [LeetCode Records](../../README.md) - Question 521 Longest Uncommon Subsequence I

### Attempt 1: Use a nested loop and contains() to test every case
```java
class Solution {
    public int findLUSlength(String a, String b) {
        String targetString = null;
        String testString = null;
        if (a.length() >= b.length()) {
            targetString = b;
            testString = a;
        } else {
            targetString = a;
            testString = b;
        }

        int n = testString.length();
        for (int i = n; i >= 1; i--) {
            for (int j = 0; j < n - i + 1; j++) {
                String substring = testString.substring(j, j + i);
                if (!targetString.contains(substring)) {
                    return i;
                }
            }
        }

        return -1;
    }
}
```
- Runtime: 2 ms (Beats: 100.00%)
- Memory: 41.88 MB (Beats: 5.91%)

<br>
