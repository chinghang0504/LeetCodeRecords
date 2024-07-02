# [LeetCode Records](../../README.md) - Question 2176 Count Equal and Divisible Pairs in an Array

### Attempt 1: Use a nested loop
```java
class Solution {
    public int countPairs(int[] nums, int k) {
        int count = 0;

        for (int i = 0; i < nums.length - 1; i++) {
            for (int j = i + 1; j < nums.length; j++) {
                if (nums[i] == nums[j] && i * j % k == 0) {
                    count++;
                }
            }
        }

        return count;
    }
}
```
- Runtime: 3 ms (Beats: 98.42%)
- Memory: 42.25 MB (Beats: 67.01%)

<br>
