# [LeetCode Records](../../README.md) - Question 1344 Angle Between Hands of a Clock

### Attempt 1: Compare with the fractions
```java
class Solution {
    public double angleClock(int hour, int minutes) {
        if (hour == 12) {
            hour = 0;
        }

        int totalMinutes = hour * 60 + minutes;
        int diffMinutes = Math.abs(totalMinutes - minutes * 12);
        double angle1 = diffMinutes / 2.0;
        double angle2 = 360.0 - angle1;
        
        return Math.min(angle1, angle2);
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 40.55 MB (Beats: 64.79%)

<br>
