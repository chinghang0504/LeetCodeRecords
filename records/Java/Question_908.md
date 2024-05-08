# [LeetCode Records](../../README.md) - Question 908 Smallest Range I

### Attempt 1: Use Arrays.sort()
```java
class Solution {
    public int smallestRangeI(int[] nums, int k) {
        Arrays.sort(nums);

        int max = nums[nums.length - 1] - k;
        int min = nums[0] + k;

        return min >= max ? 0 : max - min;
    }
}
```
- Runtime: 5 ms (Beats: 17.13%)
- Memory: 45.52 MB (Beats: 25.52%)

<br>

### Attempt 2: Use a loop to find the min and max at the same time
```java
class Solution {
    public int smallestRangeI(int[] nums, int k) {
        int maxNum = nums[0];
        int minNum = nums[0];

        for (int i = 1; i < nums.length; i++) {
            if (nums[i] > maxNum) {
                maxNum = nums[i];
            } else if (nums[i] < minNum) {
                minNum = nums[i];
            }
        }

        int max = maxNum - k;
        int min = minNum + k;

        return min >= max ? 0 : max - min;
    }
}
```
- Runtime: 1 ms (Beats: 99.13%)
- Memory: 45.28 MB (Beats: 63.29%)

<br>
