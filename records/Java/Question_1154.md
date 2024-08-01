# [LeetCode Records](../../README.md) - Question 1154 Day of the Year

### Attempt 1: Use a helper function that check if the year is a leap year
```java
class Solution {

    private int[] daysInMonth = { 31, 28, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31 };

    public int dayOfYear(String date) {
        int month = Integer.valueOf(date.substring(5, 7));
        int day = Integer.valueOf(date.substring(8, 10));
        int total = day;

        if (month == 1) {
            return total;
        } else if (month == 2) {
            return total + 31;
        }

        int year = Integer.valueOf(date.substring(0, 4));
        total = isLeapYear(year) ? total + 60 : total + 59;

        for (int i = 3; i < month; i++) {
            total += daysInMonth[i - 1];
        }

        return total;
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
- Runtime: 7 ms (Beats: 84.81%)
- Memory: 45.28 MB (Beats: 46.20%)

<br>
