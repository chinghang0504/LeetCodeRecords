# [LeetCode Records](../../README.md) - Question 1470 Shuffle the Array

### Attempt 1: 
```java
class Solution {
    public int[] shuffle(int[] nums, int n) {
        int[] result = new int[n * 2];

        for (int i = 0; i < n; i++) {
            result[i * 2] = nums[i];
            result[i * 2 + 1] = nums[i + n];
        }

        return result;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 44.70 MB (Beats: 31.63%)

<br>
