# [LeetCode Records](../../README.md) - Question 2414 Length of the Longest Alphabetical Continuous Substring

### Attempt 1: Compare the previous character
```java
class Solution {
    public int longestContinuousSubstring(String s) {
        char[] arr = s.toCharArray();
        int maxLen = 1;
        int currLen = 1;

        for (int i = 1; i < arr.length; i++) {
            if (arr[i - 1] + 1 == arr[i]) {
                currLen++;
                maxLen = Math.max(maxLen, currLen);
            } else {
                currLen = 1;
            }
        }

        return maxLen;
    }
}
```
- Runtime: 6 ms (Beats: 100.00%)
- Memory: 45.54 MB (Beats: 19.19%)

<br>
