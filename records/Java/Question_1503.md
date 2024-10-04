# [LeetCode Records](../../README.md) - Question 1503 Last Moment Before All Ants Fall Out of a Plank

### Attempt 1: Calculate the maximum of right distance and the maximum of left distance
```java
class Solution {
    public int getLastMoment(int n, int[] left, int[] right) {
        int rightDistance = 0;
        if (right.length > 0) {
            int minIndex = right[0];
            for (int i = 1; i < right.length; i++) {
                minIndex = Math.min(minIndex, right[i]);
            }

            rightDistance = n - minIndex;
        }

        int leftDistance = 0;
        if (left.length > 0) {
            int maxIndex = left[0];
            for (int i = 1; i < left.length; i++) {
                maxIndex = Math.max(maxIndex, left[i]);
            }

            leftDistance = maxIndex;
        }

        return Math.max(leftDistance, rightDistance);
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 44.80 MB (Beats: 68.42%)

<br>
