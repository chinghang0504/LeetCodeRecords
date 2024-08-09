# [LeetCode Records](../../README.md) - Question 2739 Total Distance Traveled

### Attempt 1: Use a while loop until the main tank is less than 5
```java
class Solution {
    public int distanceTraveled(int mainTank, int additionalTank) {
        int count = 0;

        while (mainTank >= 5 && additionalTank > 0) {
            additionalTank--;
            mainTank -= 4;
            count += 5;
        }

        return (count + mainTank) * 10;
    }
}
```
- Runtime: 4 ms (Beats: 99.26%)
- Memory: 43.66 MB (Beats: 88.94%)

<br>
