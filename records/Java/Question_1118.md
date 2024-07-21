# [LeetCode Records](../../README.md) - Question 1118 Number of Days in a Month

### Attempt 1: Use a helper function to check is leap year
```java
class Solution {
    public int numberOfDays(int year, int month) {
        int val = 0;
        switch (month) {
            case 1:
            case 3:
            case 5:
            case 7:
            case 8:
            case 10:
            case 12:
                val = 31;
                break;
            case 4:
            case 6:
            case 9:
            case 11:
                val = 30;
                break;
            case 2:
                val = isLeapYear(year) ? 29 : 28;
                break;
        }

        return val;
    }

    private boolean isLeapYear(int year) {
        if (year % 4 == 0) {
            if (year % 100 == 0) {
                if (year % 400 == 0) {
                    return true;
                }

                return false;
            }

            return true;
        }

        return false;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 40.14 MB (Beats: 72.73%)

<br>
