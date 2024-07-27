# [LeetCode Records](../../README.md) - Question 3000 Maximum Area of Longest Diagonal Rectangle

### Attempt 1: Compare the maximum of diagonal
```java
class Solution {
    public int areaOfMaxDiagonal(int[][] dimensions) {
        double maxDiagonal = 0.0;
        int area = 0;

        for (int[] dimension : dimensions) {
            double diagonal = Math.sqrt(dimension[0] * dimension[0] + dimension[1] * dimension[1]);
            if (diagonal > maxDiagonal) {
                maxDiagonal = diagonal;
                area = dimension[0] * dimension[1];
            } else if (diagonal == maxDiagonal) {
                area = Math.max(area, dimension[0] * dimension[1]);
            }
        }

        return area;
    }
}
```
- Runtime: 1 ms (Beats: 96.53%)
- Memory: 44.64 MB (Beats: 12.04%)

<br>
