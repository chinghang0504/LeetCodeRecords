# [LeetCode Records](../../README.md) - Question 2125 Number of Laser Beams in a Bank

### Attempt 1: Save the number of previous devices
```java
class Solution {
    public int numberOfBeams(String[] bank) {
        int prevDevices = 0;
        int sum = 0;

        for (String devices : bank) {
            int nextDevices = getNumberOfDevices(devices);
            if (nextDevices != 0) {
                sum += prevDevices * nextDevices;
                prevDevices = nextDevices;
            }
        }

        return sum;
    }

    private int getNumberOfDevices(String devices) {
        int count = 0;

        for (char ch : devices.toCharArray()) {
            if (ch == '1') {
                count++;
            }
        }

        return count;
    }
}
```
- Runtime: 10 ms (Beats: 89.86%)
- Memory: 44.94 MB (Beats: 60.09%)

<br>
