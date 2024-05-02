# [LeetCode Records](../../README.md) - Question 724 Find Pivot Index

### Attempt 1: Loop for checking the left sum and the right sum
```java
class Solution {
    public int pivotIndex(int[] nums) {
        int leftSum = 0;
        int rightSum = 0;
        for (int i = 1; i < nums.length; i++) {
            rightSum += nums[i];
        }
        int currIndex = 0;

        while (currIndex < nums.length - 1) {
            if (leftSum == rightSum) {
                return currIndex;
            } else {
                leftSum += nums[currIndex];
                currIndex++;
                rightSum -= nums[currIndex];
            }
        }

        return leftSum == rightSum ? currIndex : -1;
    }
}
```
- Runtime: 1 ms (Beats: 96.28%)
- Memory: 45.16 MB (Beats: 74.53%)

<br>
