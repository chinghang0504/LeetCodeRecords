# [LeetCode Records](../../README.md) - Question 3153 Sum of Digit Differences of All Pairs

### Attempt 1: Count the number of digits in each position
```java
class Solution {
    public long sumDigitDifferences(int[] nums) {
        long sum = 0;

        while (nums[0] > 0) {
            int[] digitCounts = new int[10];

            for (int i = 0; i < nums.length; i++) {
                digitCounts[nums[i] % 10]++;
                nums[i] /= 10;
            }

            int n = nums.length;
            for (int i = 0; i < 9 && n > 0; i++) {
                n -= digitCounts[i];
                sum += (long)digitCounts[i] * (long)n;
            }
        }

        return sum;
    }
}
```
- Runtime: 12 ms (Beats: 100.00%)
- Memory: 63.00 MB (Beats: 24.19%)

<br>
