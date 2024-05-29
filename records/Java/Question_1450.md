# [LeetCode Records](../../README.md) - Question 1450 Number of Students Doing Homework at a Given Time

### Attempt 1: Record the count
```java
class Solution {
    public int busyStudent(int[] startTime, int[] endTime, int queryTime) {
        int count = 0;
        int n = startTime.length;

        for (int i = 0; i < n; i++) {
            if (startTime[i] <= queryTime && queryTime <= endTime[i]) {
                count++;
            }
        }

        return count;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 41.47 MB (Beats: 52.24%)

<br>
