# [LeetCode Records](../../README.md) - Question 1085 Sum of Digits in the Minimum Number

### Attempt 1: Find the minimum first
```java
class Solution {
    public int sumOfDigits(int[] nums) {
        int min = nums[0];
        for (int i = 1; i < nums.length; i++) {
            min = Math.min(min, nums[i]);
        }

        int sum = 0;
        while (min > 0) {
            sum += min % 10;
            min /= 10;
        }

        return sum % 2 == 0 ? 1 : 0;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 41.20 MB (Beats: 65.85%)

<br>
