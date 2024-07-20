# [LeetCode Records](../../README.md) - Question 1995 Count Special Quadruplets

### Attempt 1: Use a nested loop
```java
class Solution {
    public int countQuadruplets(int[] nums) {
        int count = 0;

        for (int i = 0; i < nums.length - 3; i++) {
            for (int j = i + 1; j < nums.length - 2; j++) {
                for (int k = j + 1; k < nums.length - 1; k++) {
                    for (int x = k + 1; x < nums.length; x++) {
                        if (nums[i] + nums[j] + nums[k] == nums[x]) {
                            count++;
                        }
                    }
                }
            }
        }

        return count;
    }
}
```
- Runtime: 12 ms (Beats: 86.78%)
- Memory: 41.75 MB (Beats: 26.43%)

<br>
