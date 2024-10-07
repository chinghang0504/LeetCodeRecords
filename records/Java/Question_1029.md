# [LeetCode Records](../../README.md) - Question 1029 Two City Scheduling

### Attempt 1: Sum all the minimum costs and select the next lowest differences
```java
class Solution {
    public int twoCitySchedCost(int[][] costs) {
        int twoN = costs.length;
        int oneN = costs.length / 2;
        int totalCost = 0;
        boolean[] lefts = new boolean[twoN];
        int leftCount = 0;

        for (int i = 0; i < twoN; i++) {
            if (costs[i][0] <= costs[i][1]) {
                totalCost += costs[i][0];
                lefts[i] = true;
                leftCount++;
            } else {
                totalCost += costs[i][1];
            }
        }

        if (leftCount == oneN) {
            return totalCost;
        }

        if (leftCount > oneN) {
            List<Integer> list = new ArrayList<>();
            for (int i = 0; i < twoN; i++) {
                if (lefts[i]) {
                    list.add(costs[i][1] - costs[i][0]);
                }
            }
            list.sort(null);

            int step = leftCount - oneN;
            for (int i = 0; i < step; i++) {
                totalCost += list.get(i);
            }
        } else {
            List<Integer> list = new ArrayList<>();
            for (int i = 0; i < twoN; i++) {
                if (!lefts[i]) {
                    list.add(costs[i][0] - costs[i][1]);
                }
            }
            list.sort(null);

            int step = oneN - leftCount;
            for (int i = 0; i < step; i++) {
                totalCost += list.get(i);
            }
        }

        return totalCost;
    }
}
```
- Runtime: 1 ms (Beats: 98.29%)
- Memory: 42.14 MB (Beats: 10.10%)

<br>
