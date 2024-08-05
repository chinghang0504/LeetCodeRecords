# [LeetCode Records](../../README.md) - Question 2446 Determine if Two Events Have Conflict

### Attempt 1: Convert a time string to an integer
```java
class Solution {
    public boolean haveConflict(String[] event1, String[] event2) {
        int startTime1 = getTime(event1[0]);
        int endTime1 = getTime(event1[1]);
        int startTime2 = getTime(event2[0]);
        int endTime2 = getTime(event2[1]);

        return Math.max(startTime1, startTime2) <= Math.min(endTime1, endTime2);
    }

    private int getTime(String str) {
        return Integer.valueOf(str.substring(0, 2)) * 60 + Integer.valueOf(str.substring(3, 5));
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 40.83 MB (Beats: 77.21%)

<br>
