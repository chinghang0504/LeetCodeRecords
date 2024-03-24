# [LeetCode Records](../README.md) - Question 35 Search Insert Position

### Attempt 1: Search from backward
```java
class Solution {
    public int searchInsert(int[] nums, int target) {
        for (int i = nums.length - 1; i >= 0; i--) {
            if (target == nums[i]) {
                return i;
            } else if (target > nums[i]) {
                return i + 1;
            }
        }

        return 0;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 43.09 MB (Beats: 27.45%)

<br>

### Attempt 2: Binary insertion
```java
class Solution {
    public int searchInsert(int[] nums, int target) {
        return searchInsertRecursion(nums, target, 0, nums.length - 1);
    }

    private int searchInsertRecursion(int[] nums, int target, int start, int end) {
        if (end <= start) {
            return target > nums[start] ? start + 1 : start;
        }
        
        int middle = (start + end) / 2;
        if (target == nums[middle]) {
            return middle;
        } else if (target > nums[middle]) {
            return searchInsertRecursion(nums, target, middle + 1, end);
        } else {
            return searchInsertRecursion(nums, target, start, middle - 1);
        }
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 42.68 MB (Beats: 77.65%)

<br>
