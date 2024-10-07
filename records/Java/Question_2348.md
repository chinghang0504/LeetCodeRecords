# [LeetCode Records](../../README.md) - Question 2348 Number of Zero-Filled Subarrays

### Attempt 1: Use the sum of integers formula
```java
class Solution {
    public long zeroFilledSubarray(int[] nums) {
        long numOfZeros = 0;

        long currNumOfZeros = 0;
        for (int num : nums) {
            if (num == 0) {
                currNumOfZeros++;
            } else {
                numOfZeros += (1 + currNumOfZeros) * currNumOfZeros / 2;
                currNumOfZeros = 0;
            }
        }
        numOfZeros += (1 + currNumOfZeros) * currNumOfZeros / 2;

        return numOfZeros;
    }
}
```
- Runtime: 3 ms (Beats: 92.88%)
- Memory: 61.36 MB (Beats: 78.65%)

<br>
