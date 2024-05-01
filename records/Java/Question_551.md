# [LeetCode Records](../../README.md) - Question 551 Student Attendance Record I

### Attempt 1: 
```java
class Solution {
    public boolean checkRecord(String s) {
        int absentCount = 0;
        int lateCount = 0;

        for (char ch : s.toCharArray()) {
            // Absent
            if (ch == 'A') {
                absentCount++;
                if (absentCount >= 2) {
                    return false;
                }
                lateCount = 0;
            } 
            // Late
            else if (ch == 'L') {
                lateCount++;
                if (lateCount >= 3) {
                    return false;
                }
            } 
            // Present
            else {
                lateCount = 0;
            }
        }

        return true;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 41.39 MB (Beats: 59.67%)

<br>
