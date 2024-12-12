# [LeetCode Records](../../README.md) - Question 1904 The Number of Full Rounds You Have Played

### Attempt 1: Convert the time string to the time value
```java
class Solution {

    class Time {
        int hour;
        int minute;

        Time(String timeStr) {
            char[] arr = timeStr.toCharArray();
            hour = (arr[0] - '0') * 10 + arr[1] - '0';
            minute = (arr[3] - '0') * 10 + arr[4] - '0';
        }

        int compareTo(Time time) {
            if (this.hour != time.hour) {
                return this.hour - time.hour;
            } else {
                return this.minute - time.minute;
            }
        }

        void addOneDay() {
            hour += 24;
        }

        int getTimeValue() {
            return hour * 60 + minute;
        }

        void correctTime(boolean isStartTime) {
            if (isStartTime) {
                if (minute > 45) {
                    minute = 0;
                    hour++;
                } else if (minute > 30) {
                    minute = 45;
                } else if (minute > 15) {
                    minute = 30;
                } else if (minute > 0) {
                    minute = 15;
                }
            } else {
                if (minute < 15) {
                    minute = 0;
                } else if (minute < 30) {
                    minute = 15;
                } else if (minute < 45) {
                    minute = 30;
                } else {
                    minute = 45;
                }
            }
        }
    }
    public int numberOfRounds(String loginTime, String logoutTime) {
        Time startTime = new Time(loginTime);
        Time endTime = new Time(logoutTime);

        if (startTime.compareTo(endTime) > 0) {
            endTime.addOneDay();
        }

        startTime.correctTime(true);
        endTime.correctTime(false);

        int startTimeVal = startTime.getTimeValue();
        int endTimeVal = endTime.getTimeValue();
        if (startTimeVal >= endTimeVal) {
            return 0;
        } else {
            return (endTimeVal - startTimeVal) / 15;
        }
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 41.68 MB (Beats: 20.97%)

<br>
