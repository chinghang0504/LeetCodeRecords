# [LeetCode Records](../../README.md) - Question 2960 Count Tested Devices After Test Operations

### Attempt 1: Use a loop
```java
class Solution {
    public int countTestedDevices(int[] batteryPercentages) {
        int count = 0;

        for (int batteryPercentage : batteryPercentages) {
            if (batteryPercentage - count > 0) {
                count++;
            }
        }

        return count;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 43.07 MB (Beats: 41.04%)

<br>
