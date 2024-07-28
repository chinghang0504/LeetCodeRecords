# [LeetCode Records](../../README.md) - Question 746 Min Cost Climbing Stairs

### Attempt 1: Use an int[] to calculate the total cost from the left
```java
class Solution {
    public int minCostClimbingStairs(int[] cost) {
        int[] totalCost = new int[cost.length];

        for (int i = 0; i < cost.length; i++) {
            totalCost[i] = -1;
        }

        totalCost[0] = cost[0];
        totalCost[1] = cost[1];

        for (int i = 0; i < cost.length - 2; i++) {
            int cost1 = totalCost[i] + cost[i + 1];
            totalCost[i + 1] = totalCost[i + 1] == -1 ? cost1 : Math.min(totalCost[i + 1], cost1);

            int cost2 = totalCost[i] + cost[i + 2];
            totalCost[i + 2] = totalCost[i + 2] == -1 ? cost2 : Math.min(totalCost[i + 2], cost2);
        }

        return Math.min(totalCost[cost.length - 1], totalCost[cost.length - 2]);
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 42.84 MB (Beats: 70.83%)

<br>
