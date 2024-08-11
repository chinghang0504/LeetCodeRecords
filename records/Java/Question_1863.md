# [LeetCode Records](../../README.md) - Question 1863 Sum of All Subset XOR Totals

### Attempt 1: Use a recursive function to get the current sum
```java
class Solution {
    
    private int sum;
    
    public int subsetXORSum(int[] nums) {
        sum = 0;
        
        subsetXORSumRecursion(nums, 0, 0);

        return sum;
    }

    private void subsetXORSumRecursion(int[] nums, int currSum, int nextIndex) {
        if (nextIndex == nums.length) {
            return;
        }

        for (int i = nextIndex; i < nums.length; i++) {
            int nextSum = currSum ^ nums[i];
            sum += nextSum;
            subsetXORSumRecursion(nums, nextSum, i + 1);
        }
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 41.20 MB (Beats: 24.25%)

<br>
