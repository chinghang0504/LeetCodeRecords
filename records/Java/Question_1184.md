# [LeetCode Records](../../README.md) - Question 1184 Distance Between Bus Stops

### Attempt 1: Compare the clockwise and the anticlockwise distances
```java
class Solution {
    public int distanceBetweenBusStops(int[] distance, int start, int destination) {
        if (start == destination) {
            return 0;
        } else if (start > destination) {
            int temp = start;
            start = destination;
            destination = temp;
        }

        int leftDistance = 0;
        int rightDistance = 0;

        for (int i = start; i < destination; i++) {
            leftDistance += distance[i];
        }

        for (int i = start - 1; i >= 0; i--) {
            rightDistance += distance[i];
        }
        for (int i = distance.length - 1; i >= destination; i--) {
            rightDistance += distance[i];
        }

        return Math.min(leftDistance, rightDistance);
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 42.27 MB (Beats: 54.24%)

<br>
