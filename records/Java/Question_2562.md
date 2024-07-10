# [LeetCode Records](../../README.md) - Question 2562 Find the Array Concatenation Value

### Attempt 1: Use a loop
```java
class Solution {
    public long findTheArrayConcVal(int[] nums) {
        long sum = 0;

        for (int i = 0; i < nums.length / 2; i++) {
            int num1 = nums[i];
            int num2 = nums[nums.length - 1 - i];
            int multiplier = 1;
            int copy = num2;

            while (copy > 0) {
                multiplier *= 10;
                copy /= 10;
            }

            sum += num1 * multiplier + num2;
        }

        if (nums.length % 2 != 0) {
            sum += nums[nums.length / 2];
        }

        return sum;
    }
}
```
- Runtime: 1 ms (Beats: 96.36%)
- Memory: 43.12 MB (Beats: 80.77%)

<br>
