# [LeetCode Records](../../README.md) - Question 121 Best Time to Buy and Sell Stock

### Attempt 1: Loop for calculating the lowest prices and the max profit
```java
class Solution {
    public int maxProfit(int[] prices) {
        int selected = prices[0];
        int max = 0;

        for (int i = 1; i < prices.length; i++) {
            if (prices[i] < selected) {
                selected = prices[i];
            } else {
                max = Math.max(max, prices[i] - selected);
            }
        }

        return max;
    }
}
```
- Runtime: 2 ms (Beats: 79.22%)
- Memory: 61.84 MB (Beats: 23.57%)

<br>
