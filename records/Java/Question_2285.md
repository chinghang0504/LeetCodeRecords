# [LeetCode Records](../../README.md) - Question 2285 Maximum Total Importance of Roads

### Attempt 1: Use a long[] to store the node counts
```java
class Solution {
    public long maximumImportance(int n, int[][] roads) {
        long[] counts = new long[n];
        for (int[] road : roads) {
            counts[road[0]]++;
            counts[road[1]]++;
        }

        Arrays.sort(counts);

        long totalImportance = 0;
        for (int i = 0; i < n; i++) {
            totalImportance += (i + 1) * counts[i];
        }

        return totalImportance;
    }
}
```
- Runtime: 6 ms (Beats: 91.13%)
- Memory: 63.32 MB (Beats: 43.17%)

<br>
