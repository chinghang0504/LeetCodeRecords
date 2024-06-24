# [LeetCode Records](../../README.md) - Question 2798 Number of Employees Who Met the Target

### Attempt 1: Use a loop
```java
class Solution {
    public int numberOfEmployeesWhoMetTarget(int[] hours, int target) {
        int count = 0;
        
        for (int hour : hours) {
            if (hour >= target) {
                count++;
            }
        }

        return count;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 42.53 MB (Beats: 10.77%)

<br>
