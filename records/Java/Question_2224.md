# [LeetCode Records](../../README.md) - Question 2224 Minimum Number of Operations to Convert Time

### Attempt 1: Calculate the total minutes
```java
class Solution {
    public int convertTime(String current, String correct) {
        int currValue = getTotalMinutes(current);
        int corrvalue = getTotalMinutes(correct);

        int count = 0;
        while (currValue + 60 <= corrvalue) {
            currValue += 60;
            count++;
        }
        while (currValue + 15 <= corrvalue) {
            currValue += 15;
            count++;
        }
        while (currValue + 5 <= corrvalue) {
            currValue += 5;
            count++;
        }
        while (currValue + 1 <= corrvalue) {
            currValue += 1;
            count++;
        }

        return count;
    }

    private int getTotalMinutes(String time) {
        int hour = (time.charAt(0) - '0') * 10 + time.charAt(1) - '0';
        int minute = (time.charAt(3) - '0') * 10 + time.charAt(4) - '0';
        return hour * 60 + minute;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 41.22 MB (Beats: 95.40%)

<br>
