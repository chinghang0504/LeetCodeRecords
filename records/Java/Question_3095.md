# [LeetCode Records](../../README.md) - Question 3095 Shortest Subarray With OR at Least K I

### Attempt 1: Use a helper function that test every case
```java
class Solution {
    public int minimumSubarrayLength(int[] nums, int k) {
        for (int i = 1; i <= nums.length; i++) {
            for (int j = 0; j < nums.length - i + 1; j++) {
                if (isSpecial(nums, k, j, j + i)) {
                    return i;
                }
            }
        }

        return -1;
    }

    private boolean isSpecial(int[] nums, int k, int start, int end) {
        int sum = 0;

        for (int i = start; i < end; i++) {
            sum |= nums[i];
        }

        return sum >= k;
    }
}
```
- Runtime: 1 ms (Beats: 98.47%)
- Memory: 42.52 MB (Beats: 22.14%)

<br>
