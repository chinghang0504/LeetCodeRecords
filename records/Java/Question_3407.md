# [LeetCode Records](../../README.md) - Question 3407 Substring Matching Pattern

### Attempt 1: Use indexOf() to find the first index of the target string and lastIndexOf() to find the last index of the target string
```java
class Solution {
    public boolean hasMatch(String s, String p) {
        int starIndex = p.indexOf('*');

        int firstS = Integer.MIN_VALUE;
        if (starIndex != 0) {
            String firstP = p.substring(0, starIndex);
            firstS = s.indexOf(firstP);
        }
        if (firstS == -1) {
            return false;
        }

        int pLen = p.length();
        int lastS = Integer.MAX_VALUE;
        if (starIndex != pLen - 1) {
            String lastP = p.substring(starIndex + 1);
            lastS = s.lastIndexOf(lastP);
        }
        if (lastS == -1) {
            return false;
        }

        return firstS + starIndex <= lastS;
    }
}
```
- Runtime: 1 ms (Beats: 100.00%)
- Memory: 42.82 MB (Beats: 100.00%)

<br>
