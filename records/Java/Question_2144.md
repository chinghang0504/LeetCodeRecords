# [LeetCode Records](../../README.md) - Question 2144 Minimum Cost of Buying Candies With Discount

### Attempt 1: Use Array.sort() and a loop
```java
class Solution {
    public int minimumCost(int[] cost) {
        int sum = 0;
        int discountCount = 0;

        Arrays.sort(cost);

        for (int i = cost.length - 1; i >= 0; i--) {
            if (discountCount == 2) {
                discountCount = 0;
            } else {
                sum += cost[i];
                discountCount++;
            }
        }

        return sum;
    }
}
```
- Runtime: 2 ms (Beats: 96.91%)
- Memory: 42.25 MB (Beats: 32.45%)

<br>
