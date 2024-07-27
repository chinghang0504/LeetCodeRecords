# [LeetCode Records](../../README.md) - Question 2917 Find the K-or of an Array

### Attempt 1: Use an int[] to save the number of bits
```java
class Solution {
    public int findKOr(int[] nums, int k) {
        int[] counts = new int[32];

        for (int num : nums) {
            int i = 0;
            while (num > 0) {
                counts[i] += num & 1;
                num >>>= 1;
                i++;
            }
        }

        int answer = 0;
        for (int i = 31; i >= 0; i--) {
            answer <<= 1;
            answer |= counts[i] >= k ? 1 : 0;
        }

        return answer;
    }
}
```
- Runtime: 1 ms (Beats: 100.00%)
- Memory: 43.72 MB (Beats: 52.61)

<br>
