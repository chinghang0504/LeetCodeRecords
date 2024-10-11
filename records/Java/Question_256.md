# [LeetCode Records](../../README.md) - Question 256 Paint House

### Attempt 1: Calculate the minimum cumulative sum for each house
```java
class Solution {

    public int minCost(int[][] costs) {
        int[][] cumCosts = new int[costs.length][3];

        for (int j = 0; j < 3; j++) {
            cumCosts[0][j] = costs[0][j];
        }

        for (int i = 1; i < costs.length; i++) {
            cumCosts[i][0] = Integer.MAX_VALUE;
            cumCosts[i][1] = Integer.MAX_VALUE;
            cumCosts[i][2] = Integer.MAX_VALUE;

            cumCosts[i][1] = Math.min(cumCosts[i][1], cumCosts[i - 1][0] + costs[i][1]);
            cumCosts[i][2] = Math.min(cumCosts[i][2], cumCosts[i - 1][0] + costs[i][2]);

            cumCosts[i][0] = Math.min(cumCosts[i][0], cumCosts[i - 1][1] + costs[i][0]);
            cumCosts[i][2] = Math.min(cumCosts[i][2], cumCosts[i - 1][1] + costs[i][2]);

            cumCosts[i][0] = Math.min(cumCosts[i][0], cumCosts[i - 1][2] + costs[i][0]);
            cumCosts[i][1] = Math.min(cumCosts[i][1], cumCosts[i - 1][2] + costs[i][1]);
        }

        int lastIndex = costs.length - 1;
        return Math.min(cumCosts[lastIndex][0], Math.min(cumCosts[lastIndex][1], cumCosts[lastIndex][2]));
    }
}
```
- Runtime: 2 ms (Beats: 23.13%)
- Memory: 42.65 MB (Beats: 74.76%)

<br>
