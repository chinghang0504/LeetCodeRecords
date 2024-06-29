# [LeetCode Records](../../README.md) - Question 3194 Minimum Average of Smallest and Largest Elements

### Attempt 1: Use Arrays.sort()
```java
class Solution {
    public double minimumAverage(int[] nums) {
        int n = nums.length / 2;
        double[] averages = new double[n];
        int curr = 0;

        Arrays.sort(nums);

        for (int i = 0; i < n; i++) {
            averages[curr] = nums[i] + nums[nums.length - 1 - i];
            curr++;
        }

        double min = averages[0];
        for (int i = 1; i < n; i++) {
            min = Math.min(min, averages[i]);
        }

        return min / 2.0;
    }
}
```
- Runtime: 2 ms (Beats: 98.83%)
- Memory: 43.62 MB (Beats: 67.14%)

<br>
