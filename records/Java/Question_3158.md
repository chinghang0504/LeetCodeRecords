# [LeetCode Records](../../README.md) - Question 3158 Find the XOR of Numbers Which Appear Twice

### Attempt 1: Use an int[]
```java
class Solution {
    public int duplicateNumbersXOR(int[] nums) {
        int[] twiceNums = new int[51];
        
        for (int num : nums) {
            twiceNums[num]++;
        }

        int result = 0;

        for (int i = 1; i < 51; i++) {
            if (twiceNums[i] == 2) {
                result ^= i;
            }
        }

        return result;
    }
}
```
- Runtime: 1 ms (Beats: 99.47%)
- Memory: 43.13 MB (Beats: 40.95%)

<br>
