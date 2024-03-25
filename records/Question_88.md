# [LeetCode Records](../README.md) - Question 88 Merge Sorted Array

### Attempt 1: Create a new array
```java
class Solution {
    public void merge(int[] nums1, int m, int[] nums2, int n) {
        int[] nums3 = new int[m + n];
        int i = 0, j = 0, k = 0;

        while (i < m && j < n) {
            if (nums1[i] <= nums2[j]) {
                nums3[k++] = nums1[i++];
            } else {
                nums3[k++] = nums2[j++];
            }
        }
        while (i < m) {
            nums3[k++] = nums1[i++];
        }
        while (j < n) {
            nums3[k++] = nums2[j++];
        }

        System.arraycopy(nums3, 0, nums1, 0, m + n);
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 42.26 MB (Beats: 26.87%)

<br>
