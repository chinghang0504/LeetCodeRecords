# [LeetCode Records](../../README.md) - Question 713 Subarray Product Less Than K

### Attempt 1: Track the start index of the substring
```java
class Solution {
    public int numSubarrayProductLessThanK(int[] nums, int k) {
        int startIndex = 0;
        int curr = 1;
        int count = 0;

        for (int i = 0; i < nums.length; i++) {
            curr *= nums[i];
            
            while (curr >= k && startIndex <= i) {
                curr /= nums[startIndex];
                startIndex++;
            }

            count += i - startIndex + 1;
        }

        return count;
    }
}
```
- Runtime: 4 ms (Beats: 99.94%)
- Memory: 47.71 MB (Beats: 62.26%)

<br>
