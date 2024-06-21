# [LeetCode Records](../../README.md) - Question 2432 The Employee That Worked on the Longest Task

### Attempt 1: Use an int[] to record the longest work time
```java
class Solution {
    public int hardestWorker(int n, int[][] logs) {
        int[] longestWorkTime = new int[n];

        longestWorkTime[logs[0][0]] = logs[0][1];
        for (int i = 1; i < logs.length; i++) {
            longestWorkTime[logs[i][0]] = Math.max(longestWorkTime[logs[i][0]], logs[i][1] - logs[i - 1][1]);
        }

        int max = longestWorkTime[0];
        int maxId = 0;
        for (int i = 1; i < n; i++) {
            if (longestWorkTime[i] > max) {
                max = longestWorkTime[i];
                maxId = i;
            }
        }

        return maxId;
    }
}
```
- Runtime: 2 ms (Beats: 19.02%)
- Memory: 44.72 MB (Beats: 60.74%)

<br>

### Attempt 2: Use a loop
```java
class Solution {
    public int hardestWorker(int n, int[][] logs) {
        int max = logs[0][1];
        int maxId = logs[0][0];

        for (int i = 1; i < logs.length; i++) {
            int val = logs[i][1] - logs[i - 1][1];
            if (val > max) {
                max = val;
                maxId = logs[i][0];
            } else if (val == max) {
                maxId = Math.min(maxId, logs[i][0]);
            }
        }

        return maxId;
    }
}
```
- Runtime: 1 ms (Beats: 100.00%)
- Memory: 45.03 MB (Beats: 18.41%)

<br>
