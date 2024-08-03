# [LeetCode Records](../../README.md) - Question 1640 Check Array Formation Through Concatenation

### Attempt 1: Use a boolean[] to record the numbers is reached and a HashMap to record the indices of the numbers
```java
class Solution {
    public boolean canFormArray(int[] arr, int[][] pieces) {
        boolean[] reached = new boolean[arr.length];
        Map<Integer, Integer> map = new HashMap<>();

        for (int i = 0; i < arr.length; i++) {
            map.put(arr[i], i);
        }

        for (int[] nums : pieces) {
            Integer start = map.get(nums[0]);
            if (start == null) {
                return false;
            } else if (isMatched(arr, nums, start)) {
                for (int i = start; i < start + nums.length; i++) {
                    reached[i] = true;
                }
            }
        }

        for (boolean val : reached) {
            if (!val) {
                return false;
            }
        }

        return true;
    }

    private boolean isMatched(int[] arr, int[] nums, int start) {
        if (start + nums.length > arr.length) {
            return false;
        }

        for (int i = 0; i < nums.length; i++) {
            if (arr[start + i] != nums[i]) {
                return false;
            }
        }

        return true;
    }
}
```
- Runtime: 1 ms (Beats: 79.55%)
- Memory: 42.00 MB (Beats: 25.45%)

<br>
