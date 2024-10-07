# [LeetCode Records](../../README.md) - Question 973 K Closest Points to Origin

### Attempt 1: Use an int[][] to store the distance and point index relationships
```java
class Solution {
    public int[][] kClosest(int[][] points, int k) {
        int[][] distances = new int[points.length][2];
        for (int i = 0; i < points.length; i++) {
            distances[i][0] = points[i][0] * points[i][0] + points[i][1] * points[i][1];
            distances[i][1] = i;
        }

        Arrays.sort(distances, (d1, d2) -> d1[0] - d2[0]);

        int[][] ans = new int[k][2];
        for (int i = 0; i < k; i++) {
            int index = distances[i][1];
            ans[i] = points[index];
        }

        return ans;
    }
}
```
- Runtime: 29 ms (Beats: 64.15%)
- Memory: 55.57 MB (Beats: 13.17%)

<br>
