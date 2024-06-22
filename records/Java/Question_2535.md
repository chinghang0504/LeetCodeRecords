# [LeetCode Records](../../README.md) - Question 2535 Difference Between Element Sum and Digit Sum of an Array

### Attempt 1: Use a nested loop
```java
class Solution {
    public int differenceOfSum(int[] nums) {
        int elementSum = 0;
        int digitSum = 0;

        for (int num : nums) {
            elementSum += num;
            while (num > 0) {
                digitSum += num % 10;
                num /= 10;
            }
        }

        return Math.abs(elementSum - digitSum);
    }
}
```
- Runtime: 2 ms (Beats: 98.25%)
- Memory: 44.35 MB (Beats: 94.31%)

<br>
