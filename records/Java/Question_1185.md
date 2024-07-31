# [LeetCode Records](../../README.md) - Question 1185 Day of the Week

### Attempt 1: Calculate the number of days between 1971 to specific day
```java
class Solution {

    private int[] numOfDaysInMonth = { 31, 28, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31 };
    private String[] dayOfWeek = { "Sunday", "Monday", "Tuesday", "Wednesday", "Thursday", "Friday", "Saturday" };

    public String dayOfTheWeek(int day, int month, int year) {
        int totalDiff = 0;

        for (int i = 1971; i < year; i++) {
            totalDiff += isLeapYear(i) ? 366 : 365;
        }

        for (int i = 1; i < month; i++) {
            if (i == 2) {
                totalDiff += isLeapYear(year) ? 29 : 28;
            } else {
                totalDiff += numOfDaysInMonth[i - 1];
            }
        }

        totalDiff += day - 1;

        return dayOfWeek[(totalDiff + 5) % 7];
    }

    private boolean isLeapYear(int year) {
        if (year % 4 != 0) {
            return false;
        }

        if (year % 100 != 0) {
            return true;
        }

        return year % 400 == 0;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 41.18 MB (Beats: 19.74%)

<br>
