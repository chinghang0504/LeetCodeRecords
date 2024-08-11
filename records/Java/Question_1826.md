# [LeetCode Records](../../README.md) - Question 1826 Faulty Sensor

### Attempt 1: Use three while loops to test
```java
class Solution {
    public int badSensor(int[] sensor1, int[] sensor2) {
        int n = sensor1.length;
        int i = 0;

        while (i < n - 1 && sensor1[i] == sensor2[i]) {
            i++;
        }
        if (i == n - 1) {
            return -1;
        }

        boolean pass1 = false;
        boolean pass2 = false;

        int j = i + 1;
        while (j < n && sensor1[j - 1] == sensor2[j]) {
            j++;
        }
        if (j == n) {
            pass1 = true;
        }
    
        j = i + 1;
        while (j < n && sensor1[j] == sensor2[j - 1]) {
            j++;
        }
        if (j == n) {
            pass2 = true;
        }

        if (pass1 && pass2) {
            return -1;
        } else if (pass1) {
            return 1;
        } else if (pass2) {
            return 2;
        } else {
            return -1;
        }
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 42.12 MB (Beats: 62.62%)

<br>
