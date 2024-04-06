# [LeetCode Records](../README.md) - Question 392 Is Subsequence

### Attempt 1: Use two char arrays
```java
class Solution {
    public boolean isSubsequence(String s, String t) {
        char[] sCharArr = s.toCharArray();
        char[] tCharArr = t.toCharArray();

        int sIndex = 0;
        int tIndex = 0;
        for (; sIndex < sCharArr.length && tIndex < tCharArr.length; tIndex++) {
            if (sCharArr[sIndex] == tCharArr[tIndex]) {
                sIndex++;
            }
        }

        return sIndex == sCharArr.length;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 41.76 MB (Beats: 9.32%)

<br>
