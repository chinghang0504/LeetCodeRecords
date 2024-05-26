# [LeetCode Records](../../README.md) - Question 1313 Decompress Run-Length Encoded List

### Attempt 1: Get the size of the array first
```java
class Solution {
    public int[] decompressRLElist(int[] nums) {
        int count = 0;
        for (int i = 0; i < nums.length; i += 2) {
            count += nums[i];
        }

        int[] result = new int[count];
        int curr = 0;
        for (int i = 0; i < nums.length; i += 2) {
            for (int j = 0; j < nums[i]; j++) {
                result[curr] = nums[i + 1];
                curr++;
            }
        }

        return result;
    }
}
```
- Runtime: 2 ms (Beats: 75.45%)
- Memory: 44.81 MB (Beats: 62.45%)

<br>
