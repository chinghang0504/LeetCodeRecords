# [LeetCode Records](../../README.md) - Question 3238 Find the Number of Winning Players

### Attempt 1: Use an int[][] to record the ball counts
```java
class Solution {
    public int winningPlayerCount(int n, int[][] pick) {
        int[][] counts = new int[n][11];

        for (int[] item : pick) {
            counts[item[0]][item[1]]++;
        }

        int count = 0;
        for (int i = 0; i < n; i++) {
            int target = i + 1;
            for (int record : counts[i]) {
                if (record >= target) {
                    count++;
                    break;
                }
            }
        }

        return count;
    }
}
```
- Runtime: 1 ms (Beats: 100.00%)
- Memory: 45.24 MB (Beats: 100.00%)

<br>
