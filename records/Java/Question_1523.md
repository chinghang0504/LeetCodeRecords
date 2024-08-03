# [LeetCode Records](../../README.md) - Question 1523 Count Odd Numbers in an Interval Range

### Attempt 1: Check if the low and the high are odd numbers
```java
class Solution {
    public int countOdds(int low, int high) {
        boolean isLowOdd = low % 2 == 1;
        boolean isHighOdd = high % 2 == 1;

        if (isLowOdd && isHighOdd) {
            return (high - low) / 2 + 1;
        } else if (isLowOdd || isHighOdd) {
            return (high + 1 - low) / 2;
        } else {
            return (high - low) / 2;
        }
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 40.15 MB (Beats: 63.03%)

<br>
