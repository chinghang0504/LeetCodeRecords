# [LeetCode Records](../README.md) - Question 163 Missing Ranges

### Attempt 1: Check the range at each time
```java
class Solution {
    public List<List<Integer>> findMissingRanges(int[] nums, int lower, int upper) {
        List<List<Integer>> result = new ArrayList<>();

        if (nums.length == 0) {
            result.add(List.of(lower, upper));
            return result;
        }

        if (lower < nums[0]) {
            result.add(List.of(lower, nums[0] - 1));
        }

        for (int i = 0; i < nums.length - 1; i++) {
            if (nums[i] != nums[i + 1] - 1) {
                int start = nums[i] + 1;
                int end = nums[i + 1] - 1;

                if (end < lower) {
                    continue;
                } else if (start > upper) {
                    continue;
                }

                if (start < lower) {
                    start = lower;
                }
                if (end > upper) {
                    end = upper;
                }

                result.add(List.of(start, end));
            }
        }

        if (upper > nums[nums.length - 1]) {
            result.add(List.of(nums[nums.length - 1] + 1, upper));
        }

        return result;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 41.33 MB (Beats: 42.72%)

<br>
