# [LeetCode Records](../../README.md) - Question 3354 Make Array Elements Equal to Zero

### Attempt 1: Test every possible case
```java
class Solution {
    public int countValidSelections(int[] nums) {
        int[] copyNums = Arrays.copyOf(nums, nums.length);
        int count = 0;

        for (int i = 0; i < nums.length; i++) {
            if (nums[i] == 0) {
                if (isValid(copyNums, i, true)) {
                    count++;
                }
                for (int j = 0; j < nums.length; j++) {
                    copyNums[j] = nums[j];
                }

                if (isValid(copyNums, i, false)) {
                    count++;
                }
                for (int j = 0; j < nums.length; j++) {
                    copyNums[j] = nums[j];
                }
            }
        }

        return count;
    }

    private boolean isValid(int[] nums, int curr, boolean isLeft) {
        while (true) {
            if (isLeft) {
                curr--;
            } else {
                curr++;
            }

            if (curr < 0 || curr == nums.length) {
                break;
            } else if (nums[curr] > 0) {
                nums[curr]--;
                isLeft = !isLeft;
            }
        }

        for (int i = 0; i < nums.length; i++) {
            if (nums[i] != 0) {
                return false;
            }
        }

        return true;
    }
}
```
- Runtime: 108 ms (Beats: 100.00%)
- Memory: 42.03 MB (Beats: 100.00%)

<br>
