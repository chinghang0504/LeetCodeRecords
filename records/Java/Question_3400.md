# [LeetCode Records](../../README.md) - Question 3400 Maximum Number of Matching Indices After Right Shifts

### Attempt 1: Test every case
```java
class Solution {
    public int maximumMatchingIndices(int[] nums1, int[] nums2) {
        int maxCount = 0;

        for (int i = 0; i < nums1.length; i++) {
            int count = 0;
            
            for (int j = 0; j < nums2.length; j++) {
                if (nums1[(i + j) % nums1.length] == nums2[j]) {
                    count++;
                }
            }

            maxCount = Math.max(maxCount, count);
        }

        return maxCount;
    }
}
```
- Runtime: 86 ms (Beats: 100.00%)
- Memory: 44.95 MB (Beats: 100.00%)

<br>
