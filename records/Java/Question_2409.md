# [LeetCode Records](../../README.md) - Question 2409 Count Days Spent Together

### Attempt 1: Calculate the total nubmer of days for each date
```java
class Solution {

    private int[] daysInMonth = { 31, 28, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31 };

    public int countDaysTogether(String arriveAlice, String leaveAlice, String arriveBob, String leaveBob) {
        int arriveAliceTotalDay = getTotalDay(arriveAlice);
        int leaveAliceTotalDay = getTotalDay(leaveAlice);
        int arriveBobTotalDay = getTotalDay(arriveBob);
        int leaveBobTotalDay = getTotalDay(leaveBob);

        int start = Math.max(arriveAliceTotalDay, arriveBobTotalDay);
        int end = Math.min(leaveAliceTotalDay, leaveBobTotalDay);
        int diff = end - start;

        return diff < 0 ? 0 : diff + 1;
    }

    private int getTotalDay(String date) {
        int month = Integer.valueOf(date.substring(0, 2));
        int day = Integer.valueOf(date.substring(3, 5));
        int totalDay = 0;

        for (int i = 1; i < month; i++) {
            totalDay += daysInMonth[i - 1];
        }
        totalDay += day;

        return totalDay;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 41.30 MB (Beats: 70.90%)

<br>
