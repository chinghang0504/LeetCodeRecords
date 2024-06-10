# [LeetCode Records](../../README.md) - Question 1672 Richest Customer Wealth

### Attempt 1: Use two loops
```java
class Solution {
    public int maximumWealth(int[][] accounts) {
        int max = 0;

        for (int[] account : accounts) {
            int sum = 0;
            for (int amount : account) {
                sum += amount;
            }
            max = Math.max(max, sum);
        }

        return max;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 43.04 MB (Beats: 8.97%)

<br>
