# [LeetCode Records](../../README.md) - Question 1637 Widest Vertical Area Between Two Points Containing No Points

### Attempt 1: 
```java
class Solution {
    public int maxWidthOfVerticalArea(int[][] points) {
        int[] values = new int[points.length];
        int size = 0;
        for (int[] point : points) {
            values[size] = point[0];
            size++;
        }

        Arrays.sort(values);

        int maxDiff = 0;
        for (int i = 1; i < size; i++) {
            int diff = values[i] - values[i - 1];
            maxDiff = Math.max(maxDiff, diff);
        }

        return maxDiff;
    }
}
```
- Runtime: 13 ms (Beats: 96.35%)
- Memory: 73.49 MB (Beats: 9.76%)

<br>
