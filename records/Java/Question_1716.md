# [LeetCode Records](../../README.md) - Question 1716 Calculate Money in Leetcode Bank

### Attempt 1: Use a nested loop to calculate the total
```java
class Solution {
    public int totalMoney(int n) {
        int day = 0;
        int weekStart = 0;
        int total = 0;

        while (day < n) {
            weekStart++;

            int minDay = Math.min(7, n - day);
            for (int i = 0; i < minDay; i++) {
                total += weekStart + i;
            }

            day += minDay;
        }

        return total;
    }
}
```
- Runtime: 1 ms (Beats: 59.95%)
- Memory: 40.32 MB (Beats: 36.07%)

<br>
