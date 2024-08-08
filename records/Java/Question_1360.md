# [LeetCode Records](../../README.md) - Question 1360 Number of Days Between Two Dates

### Attempt 1: Calculate the total number of day from 1971
```java
class Solution {

    private int[] daysInMonth = { 31, 28, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31 };

    public int daysBetweenDates(String date1, String date2) {
        return Math.abs(getTotalDay(date1) - getTotalDay(date2));
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

    private int getTotalDay(String date) {
        int year = Integer.valueOf(date.substring(0, 4));
        int month = Integer.valueOf(date.substring(5, 7));
        int day = Integer.valueOf(date.substring(8, 10));
        int totalDay = 0;

        for (int i = 1971; i < year; i++) {
            totalDay += isLeapYear(i) ? 366 : 365;
        }

        for (int i = 1; i < month; i++) {
            totalDay += daysInMonth[i - 1];
        }
        if (month > 2 && isLeapYear(year)) {
            totalDay++;
        }

        totalDay += day;

        return totalDay;
    }
}
```
- Runtime: 1 ms (Beats: 94.93%)
- Memory: 40.90 MB (Beats: 98.39%)

<br>
