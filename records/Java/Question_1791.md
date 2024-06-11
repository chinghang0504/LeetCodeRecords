# [LeetCode Records](../../README.md) - Question 1791 Find Center of Star Graph

### Attempt 1: Compare the first two points
```java
class Solution {
    public int findCenter(int[][] edges) {
        int point1 = edges[0][0];
        int point2 = edges[0][1];
        int point3 = edges[1][0];
        int point4 = edges[1][1];

        return (point1 == point3 || point1 == point4) ? point1 : point2;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 66.78 MB (Beats: 71.55%)

<br>
