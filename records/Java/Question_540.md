# [LeetCode Records](../../README.md) - Question 540 Single Element in a Sorted Array

### Attempt 1: Calculate the sum of xor
```java
class Solution {
    public int singleNonDuplicate(int[] nums) {
        int xorSum = 0;
        
        for (int num : nums) {
            xorSum ^= num;
        }

        return xorSum;
    }
}
```
- Runtime: 1 ms (Beats: 28.15%)
- Memory: 50.39 MB (Beats: 31.21%)

<br>
