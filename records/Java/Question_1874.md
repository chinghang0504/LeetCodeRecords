# [LeetCode Records](../../README.md) - Question 1874 Minimize Product Sum of Two Arrays

### Attempt 1: Use two Arrays.sort() and a loop
```java
class Solution {
    public int minProductSum(int[] nums1, int[] nums2) {
        Arrays.sort(nums1);
        Arrays.sort(nums2);

        int sum = 0;
        int n = nums1.length;
        for (int i = 0; i < n; i++) {
            sum += nums1[i] * nums2[n - 1 - i];
        }

        return sum;
    }
}
```
- Runtime: 22 ms (Beats: 84.40%)
- Memory: 64.75 MB (Beats: 13.76%)

<br>
