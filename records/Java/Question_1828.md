# [LeetCode Records](../../README.md) - Question 1828 Queries on Number of Points Inside a Circle

### Attempt 1: Test each point
```java
class Solution {
    public int[] countPoints(int[][] points, int[][] queries) {
        int[] answer = new int[queries.length];

        for (int i = 0; i < queries.length; i++) {
            for (int[] point : points) {
                int xDiff = Math.abs(point[0] - queries[i][0]);
                int yDiff = Math.abs(point[1] - queries[i][1]);
                int radius = queries[i][2];

                if (xDiff * xDiff + yDiff * yDiff <= radius * radius) {
                    answer[i]++;
                }
            }
        }

        return answer;
    }
}
```
- Runtime: 35 ms (Beats: 34.85%)
- Memory: 45.16 MB (Beats: 46.68%)

<br>

### Attempt 2: Save the square of the radius
```java
class Solution {
    public int[] countPoints(int[][] points, int[][] queries) {
        int[] answer = new int[queries.length];

        for (int i = 0; i < queries.length; i++) {
            int radius = queries[i][2];
            int radiusSquare = radius * radius;

            for (int[] point : points) {
                int xDiff = Math.abs(point[0] - queries[i][0]);
                int yDiff = Math.abs(point[1] - queries[i][1]);
                

                if (xDiff * xDiff + yDiff * yDiff <= radiusSquare) {
                    answer[i]++;
                }
            }
        }

        return answer;
    }
}
```
- Runtime: 34 ms (Beats: 37.97%)
- Memory: 45.33 MB (Beats: 16.18%)

<br>
