# [LeetCode Records](../../README.md) - Question 3232 Find if Digit Game Can Be Won

### Attempt 1: Use two variables to save the sums
```java
class Solution {
    public boolean canAliceWin(int[] nums) {
        int singleDigitSum = 0;
        int doubleDigitsSum = 0;

        for (int num : nums) {
            if (num >= 10) {
                doubleDigitsSum += num;
            } else {
                singleDigitSum  += num;
            }
        }

        return singleDigitSum != doubleDigitsSum;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 44.06 MB (Beats: 100.00%)

<br>
