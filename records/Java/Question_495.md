# [LeetCode Records](../../README.md) - Question 495 Teemo Attacking

### Attempt 1: Calculate the time difference bewteen t and t+1
```java
class Solution {
    public int findPoisonedDuration(int[] timeSeries, int duration) {
        int count = 0;

        for (int i = 0; i < timeSeries.length - 1; i++) {
            int diff = timeSeries[i + 1] - timeSeries[i];
            if (diff < duration) {
                count += diff;
            } else {
                count += duration;
            }
        }
        count += duration;

        return count;
    }
}
```
- Runtime: 3 ms (Beats: 82.11%)
- Memory: 45.42 MB (Beats: 7.58%)

<br>
