# [LeetCode Records](../../README.md) - Question 2997 Minimum Number of Operations to Make Array XOR Equal to K

### Attempt 1: Get the xor sum of all the elements and compare to the k value
```java
class Solution {
    public int minOperations(int[] nums, int k) {
        int xorSum = nums[0];
        for (int i = 1; i < nums.length; i++) {
            xorSum ^= nums[i];
        }

        int count = 0;
        while (k != 0 || xorSum != 0) {
            if ((k & 1) != (xorSum & 1)) {
                count++;
            }

            k >>>= 1;
            xorSum >>>= 1;
        }

        return count;
    }
}
```
- Runtime: 1 ms (Beats: 100.00%)
- Memory: 58.33 MB (Beats: 39.14%)

<br>
