# [LeetCode Records](../../README.md) - Question 31 Next Permutation

### Attempt 1: Find the previous decreasing number
```java
class Solution {
    public void nextPermutation(int[] nums) {
        if (!swapNum(nums)) {
            reverseArr(nums, 0, nums.length - 1);
        }
    }

    private boolean swapNum(int[] nums) {
        for (int i = nums.length - 1; i >= 1; i--) {
            if (nums[i - 1] < nums[i]) {
                int minVal = Integer.MAX_VALUE;
                int minValIndex = i;
                for (int j = i; j < nums.length; j++) {
                    if (nums[i - 1] < nums[j] && nums[j] <= minVal) {
                        minVal = nums[j];
                        minValIndex = j;
                    }
                }

                int temp = nums[i - 1];
                nums[i - 1] = nums[minValIndex];
                nums[minValIndex] = temp;

                reverseArr(nums, i, nums.length - 1);
                return true;
            }
        }

        return false;
    }

    private void reverseArr(int[] nums, int start, int end) {
        while (start < end) {
            int temp = nums[start];
            nums[start] = nums[end];
            nums[end] = temp;

            start++;
            end--;
        }
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 42.78 MB (Beats: 91.88%)

<br>
