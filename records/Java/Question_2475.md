# [LeetCode Records](../../README.md) - Question 2475 Number of Unequal Triplets in Array

### Attempt 1: Use a nested loop
```java
class Solution {
    public int unequalTriplets(int[] nums) {
        int count = 0;
        int n = nums.length;

        for (int i = 0; i < n - 2; i++) {
            for (int j = i + 1; j < n - 1; j++) {
                if (nums[i] == nums[j]) {
                    continue;
                }

                for (int k = j + 1; k < n; k++) {
                    if (nums[j] == nums[k] || nums[i] == nums[k]) {
                        continue;
                    }

                    count++;
                }
            }
        }

        return count;
    }
}
```
- Runtime: 6 ms (Beats: 89.01%)
- Memory: 40.98 MB (Beats: 70.04%)

<br>
