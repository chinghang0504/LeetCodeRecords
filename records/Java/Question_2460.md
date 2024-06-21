# [LeetCode Records](../../README.md) - Question 2460 Apply Operations to an Array

### Attempt 1: Use two loops
```java
class Solution {
    public int[] applyOperations(int[] nums) {
        for (int i = 0; i < nums.length - 1; i++) {
            if (nums[i] == nums[i + 1]) {
                nums[i] *= 2;
                nums[i + 1] = 0;
            }
        }

        int curr = 0;
        int[] result = new int[nums.length];
        for (int i = 0; i < nums.length; i++) {
            if (nums[i] != 0) {
                result[curr] = nums[i];
                curr++;
            }
        }

        return result;
    }
}
```
- Runtime: 1 ms (Beats: 92.46%)
- Memory: 43.76 MB (Beats: 39.41%)

<br>
