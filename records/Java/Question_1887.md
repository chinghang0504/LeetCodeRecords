# [LeetCode Records](../../README.md) - Question 1887 Reduction Operations to Make the Array Elements Equal

### Attempt 1: Use Arrays.sort() to sort the array first
```java
class Solution {
    public int reductionOperations(int[] nums) {
        Arrays.sort(nums);

        int leftIndex = 1;
        while (leftIndex < nums.length && nums[leftIndex] == nums[0]) {
            leftIndex++;
        }

        int sum = 0;
        while (leftIndex < nums.length) {
            sum += nums.length - leftIndex;

            int target = nums[leftIndex];
            leftIndex++;
            while (leftIndex < nums.length && nums[leftIndex] == target) {
                leftIndex++;
            }
        }

        return sum;
    }
}
```
- Runtime: 34 ms (Beats: 63.03%)
- Memory: 56.07 MB (Beats: 46.22%)

<br>
