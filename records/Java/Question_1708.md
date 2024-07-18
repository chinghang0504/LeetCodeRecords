# [LeetCode Records](../../README.md) - Question 1708 Largest Subarray Length K

### Attempt 1: Use a helper function that compares arrays
```java
class Solution {
    public int[] largestSubarray(int[] nums, int k) {
        int maxStartIndex = 0;

        for (int i = 1; i <= nums.length - k; i++) {
            if (compareSubarray(nums, k, i, maxStartIndex) == 1) {
                maxStartIndex = i;
            }
        }

        int[] answer = new int[k];
        for (int i = 0; i < k; i++) {
            answer[i] = nums[maxStartIndex + i];
        }

        return answer;
    }

    private int compareSubarray(int[] nums, int k, int leftStartIndex, int rightStartIndex) {
        for (int i = 0; i < k; i++) {
            if (nums[leftStartIndex + i] > nums[rightStartIndex + i]) {
                return 1;
            } else if (nums[leftStartIndex + i] < nums[rightStartIndex + i]) {
                return -1;
            }
        }

        return 0;
    }
}
```
- Runtime: 3 ms (Beats: 15.79%)
- Memory: 55.26 MB (Beats: 77.19%)

<br>
