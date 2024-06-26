# [LeetCode Records](../../README.md) - Question 2651 Calculate Delayed Arrival Time

### Attempt 1: 
```java
class Solution {
    public int findDelayedArrivalTime(int arrivalTime, int delayedTime) {
        int time = arrivalTime + delayedTime;
        return time >= 24 ? time - 24 : time;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 40.42 MB (Beats: 55.00%)

<br>
