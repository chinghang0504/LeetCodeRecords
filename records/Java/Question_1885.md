# [LeetCode Records](../../README.md) - Question 1885 Count Pairs in Two Arrays

### Attempt 1: Use binary search to find the target number
```java
class Solution {
    public long countPairs(int[] nums1, int[] nums2) {
        int n = nums1.length;

        int[] diffs = new int[n];
        for (int i = 0; i < n; i++) {
            diffs[i] = nums1[i] - nums2[i];
        }
        Arrays.sort(diffs);

        long count = 0;
        for (int i = 0; i < n - 1; i++) {
            if (diffs[i] > 0) {
                count += n - i - 1;
                continue;
            }

            int left = i + 1;
            int right = n - 1;
            while (left <= right) {
                int mid = left + (right - left) / 2;
                if (diffs[i] + diffs[mid] > 0) {
                    right = mid - 1;
                } else {
                    left = mid + 1;
                }
            }

            count += n - left;
        }

        return count;
    }
}
```
- Runtime: 37 ms (Beats: 38.46%)
- Memory: 59.10 MB (Beats: 46.15%)

<br>
