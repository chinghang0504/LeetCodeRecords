# [LeetCode Records](../../README.md) - Question 2706 Buy Two Chocolates

### Attempt 1: Use Arrays.sort()
```java
class Solution {
    public int buyChoco(int[] prices, int money) {
        Arrays.sort(prices);

        int total = prices[0] + prices[1];
        return total <= money ? money - total : money;
    }
}
```
- Runtime: 2 ms (Beats: 72.66%)
- Memory: 44.25 MB (Beats: 41.33%)

<br>
