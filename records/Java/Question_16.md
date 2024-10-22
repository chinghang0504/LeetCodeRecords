# [LeetCode Records](../../README.md) - Question 16 3Sum Closest

### Attempt 1: Use two fop loops and binary search
```java
class Solution {
    public int threeSumClosest(int[] nums, int target) {
        Arrays.sort(nums);

        int closedSum = Integer.MAX_VALUE;
        int closedDiff = Integer.MAX_VALUE;

        for (int i = 0; i < nums.length - 2; i++) {
            int num1 = nums[i];

            for (int j = i + 1; j < nums.length - 1; j++) {
                int num2 = nums[j];
                int expectedNum3 = target - num1 - num2;
                int num3 = getClosedTargetNum(nums, target - num1 - num2, j + 1);
                int diff = Math.abs(expectedNum3 - num3);

                if (diff == 0) {
                    return target;
                } else if (diff < closedDiff) {
                    closedDiff = diff;
                    closedSum = num1 + num2 + num3;
                }
            }
        }

        return closedSum;
    }

    private int getClosedTargetNum(int[] nums, int target, int low) {
        int high = nums.length - 1;

        while (high - low > 1) {
            int middle = (low + high) / 2;

            if (nums[middle] == target) {
                return nums[middle];
            } else if (nums[middle] > target) {
                high = middle;
            } else {
                low = middle;
            }
        }

        int diff1 = Math.abs(nums[low] - target);
        int diff2 = Math.abs(nums[high] - target);

        return diff1 < diff2 ? nums[low] : nums[high];
    }
}
```
- Runtime: 67 ms (Beats: 11.29%)
- Memory: 43.35 MB (Beats: 24.35%)

<br>
