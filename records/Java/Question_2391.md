# [LeetCode Records](../../README.md) - Question 2391 Minimum Amount of Time to Collect Garbage

### Attempt 1: Convert the String[] garbage to an int[][]
```java
class Solution {
    public int garbageCollection(String[] garbage, int[] travel) {
        int[][] allCounts = new int[3][garbage.length];

        for (int i = 0; i < garbage.length; i++) {
            for (char ch : garbage[i].toCharArray()) {
                if (ch == 'G') {
                    allCounts[0][i]++;
                } else if (ch == 'M') {
                    allCounts[1][i]++;
                } else if (ch == 'P') {
                    allCounts[2][i]++;
                }
            }
        }

        int totalTime = 0;
        for (int i = 0; i < 3; i++) {
            totalTime += allCounts[i][0];

            int travelTime = 0;
            for (int j = 1; j < garbage.length; j++) {
                travelTime += travel[j - 1];
                if (allCounts[i][j] > 0) {
                    totalTime += allCounts[i][j] + travelTime;
                    travelTime = 0;
                }
            }
        }

        return totalTime;
    }
}
```
- Runtime: 25 ms (Beats: 56.26%)
- Memory: 68.50 MB (Beats: 29.52%)

<br>
