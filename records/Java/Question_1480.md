# [LeetCode Records](../../README.md) - Question 1480 Running Sum of 1d Array

### Attempt 1: Clone the array first
```java
class Solution {
    public int[] runningSum(int[] nums) {
        int[] result = nums.clone();

        for (int i = 1; i < nums.length; i++) {
            result[i] += result[i - 1];
        }

        return result;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 43.04 MB (Beats: 9.77%)

<br>
