# [LeetCode Records](../../README.md) - Question 1689 Partitioning Into Minimum Number Of Deci-Binary Numbers

### Attempt 1: Get the maximum digit
```java
class Solution {
    public int minPartitions(String n) {
        int maxDigit = 0;

        for (char ch : n.toCharArray()) {
            maxDigit = Math.max(maxDigit, (ch - '0'));
        }

        return maxDigit;
    }
}
```
- Runtime: 5 ms (Beats: 75.33%)
- Memory: 45.05 MB (Beats: 50.73%)

<br>
