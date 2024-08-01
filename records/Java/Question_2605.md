# [LeetCode Records](../../README.md) - Question 2605 Form Smallest Number From Two Digit Arrays

### Attempt 1: Use two Arrays.sort() and find the minimum common integer
```java
class Solution {
    public int minNumber(int[] nums1, int[] nums2) {
        Arrays.sort(nums1);
        Arrays.sort(nums2);

        int minDigit = getMinDigit(nums1, nums2);

        if (minDigit != -1) {
            return minDigit;
        }

        return nums1[0] <= nums2[0] ? nums1[0] * 10 + nums2[0] : nums2[0] * 10 + nums1[0];
    }

    private int getMinDigit(int[] nums1, int[] nums2) {
        for (int i = 0; i < nums1.length; i++) {
            for (int j = 0; j < nums2.length; j++) {
                if (nums1[i] == nums2[j]) {
                    return nums1[i];
                } else if (nums1[i] < nums2[j]) {
                    break;
                }
            }
        }

        return -1;
    }
}
```
- Runtime: 1 ms (Beats: 87.68%)
- Memory: 41.96 MB (Beats: 12.09%)

<br>
