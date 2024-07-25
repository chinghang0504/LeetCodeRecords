# [LeetCode Records](../../README.md) - Question 3184 Count Pairs That Form a Complete Day I

### Attempt 1: Use a nested loop
```java
class Solution {
    public int countCompleteDayPairs(int[] hours) {
        int count = 0;

        for (int i = 0; i < hours.length - 1; i++) {
            for (int j = i + 1; j < hours.length; j++) {
                if ((hours[i] + hours[j]) % 24 == 0) {
                    count++;
                }
            }
        }

        return count;
    }
}
```
- Runtime: 1 ms (Beats: 98.16%)
- Memory: 42.44 MB (Beats: 31.94%)

<br>
