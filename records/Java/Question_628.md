# [LeetCode Records](../../README.md) - Question 628 Maximum Product of Three Numbers

### Attempt 1: Use Arrays.sort() to sort numbers
```java
class Solution {
    public int maximumProduct(int[] nums) {
        Arrays.sort(nums);

        int product1 = nums[nums.length - 1] * nums[nums.length - 2] * nums[nums.length - 3];
        int product2 = nums[0] * nums[1] * nums[nums.length - 1];

        return Math.max(product1, product2);
    }
}
```
- Runtime: 11 ms (Beats: 81.18%)
- Memory: 45.53 MB (Beats: 36.65%)

<br>
