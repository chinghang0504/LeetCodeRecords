# [LeetCode Records](../../README.md) - Question 1991 Find the Middle Index in Array

### Attempt 1: 
```java
class Solution {
    public int findMiddleIndex(int[] nums) {
        int leftSum = 0;
        int rightSum = 0;
        int middleIndex = 0;

        for (int i = 1; i < nums.length; i++) {
            rightSum += nums[i];
        }

        while (middleIndex < nums.length - 1) {
            if (leftSum == rightSum) {
                return middleIndex;
            } else {
                leftSum += nums[middleIndex];
                rightSum -= nums[middleIndex + 1];
                middleIndex++;
            }
        }
        if (leftSum == 0) {
            return middleIndex;
        }

        return -1;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 42.08 MB (Beats: 11.65%)

<br>
