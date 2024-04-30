# [LeetCode Records](../README.md) - Question 704 Binary Search

### Attempt 1: Use recursion
```java
class Solution {
    public int search(int[] nums, int target) {
        return searchRecursion(nums, target, 0, nums.length - 1);
    }

    private int searchRecursion(int[] nums, int target, int start, int end) {
        if (start > end) {
            return -1;
        }

        int middle = (start + end) / 2;
        if (target == nums[middle]) {
            return middle;
        } else if (target < nums[middle]) {
            return searchRecursion(nums, target, start, middle - 1);
        } else {
            return searchRecursion(nums, target, middle + 1, end);
        }
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 45.81 MB (Beats: 21.15%)

<br>
