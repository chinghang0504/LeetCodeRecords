# [LeetCode Records](../../README.md) - Question 3131 Find the Integer Added to Array I

### Attempt 1: Find the minimum integer in each array
```java
class Solution {
    public int addedInteger(int[] nums1, int[] nums2) {
        int min1 = nums1[0];
        for (int i = 1; i < nums1.length; i++) {
            min1 = Math.min(min1, nums1[i]);
        }

        int min2 = nums2[0];
        for (int i = 1; i < nums2.length; i++) {
            min2 = Math.min(min2, nums2[i]);
        }

        return min2 - min1;
    }
}
```
- Runtime: 1 ms (Beats: 70.93%)
- Memory: 42.81 MB (Beats: 63.09%)

<br>
