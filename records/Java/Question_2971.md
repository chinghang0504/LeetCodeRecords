# [LeetCode Records](../../README.md) - Question 2971 Find Polygon With the Largest Perimeter

### Attempt 1: Use Arrays.sort() to sort the array and search from the longest side
```java
class Solution {
    public long largestPerimeter(int[] nums) {
        Arrays.sort(nums);

        long perimeter = 0;
        for (int num : nums) {
            perimeter += num;
        }

        for (int i = nums.length - 1; i >= 2; i--) {
            long nextPerimeter = perimeter - nums[i];
            if (nums[i] < nextPerimeter) {
                return perimeter;
            }
            perimeter = nextPerimeter;
        }

        return -1;
    }
}
```
- Runtime: 29 ms (Beats: 61.19%)
- Memory: 56.16 MB (Beats: 85.31%)

<br>
