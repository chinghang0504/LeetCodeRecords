# [LeetCode Records](../../README.md) - Question 1342 Number of Steps to Reduce a Number to Zero

### Attempt 1: 
```java
class Solution {
    public int numberOfSteps(int num) {
        int stepCount = 0;

        while (num != 0) {
            if (num % 2 == 0) {
                num /= 2;
            } else {
                num -= 1;
            }

            stepCount++;
        }

        return stepCount;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 40.24 MB (Beats: 59.93%)

<br>
