# [LeetCode Records](../../README.md) - Question 4 Median of Two Sorted Arrays

### Attempt 1: Form an array
```java
class Solution {
    public double findMedianSortedArrays(int[] nums1, int[] nums2) {
        int total = nums1.length + nums2.length;
        int[] nums = new int[total];
        int curr = 0, i = 0, j = 0;

        for (; i < nums1.length && j < nums2.length; curr++) {
            nums[curr] = nums1[i] <= nums2[j] ? nums1[i++] : nums2[j++];
        }
        for (; i < nums1.length; curr++) {
            nums[curr] = nums1[i++];
        }
        for (; j < nums2.length; curr++) {
            nums[curr] = nums2[j++];
        }

        boolean odd = total % 2 == 1;
        int index = total / 2;
        if (odd) {
            return nums[index];
        } else {
            return (nums[index-1] + nums[index]) / 2.0;
        }
    }
}
```
- Runtime: 1 ms (Beats: 100.00%)
- Memory: 45.37 MB (Beats: 98.30%)

<br>

### Attemp 2: Terminate when reaching the index
```java
class Solution {
    public double findMedianSortedArrays(int[] nums1, int[] nums2) {
        int total = nums1.length + nums2.length;
        int index = total / 2;
        int[] nums = new int[index + 1];
        int curr = 0, i = 0, j = 0;

        for (; i < nums1.length && j < nums2.length && curr <= index; curr++) {
            nums[curr] = nums1[i] <= nums2[j] ? nums1[i++] : nums2[j++];
        }
        for (; i < nums1.length && curr <= index; curr++) {
            nums[curr] = nums1[i++];
        }
        for (; j < nums2.length && curr <= index; curr++) {
            nums[curr] = nums2[j++];
        }

        boolean odd = total % 2 == 1;
        if (odd) {
            return nums[index];
        } else {
            return (nums[index-1] + nums[index]) / 2.0;
        }
    }
}
```
- Runtime: 2 ms (Beats: 65.24%)
- Memory: 46.08 MB (Beats: 39.31%)

<br>
