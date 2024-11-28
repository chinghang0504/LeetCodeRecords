# [LeetCode Records](../../README.md) - Question 477 Total Hamming Distance

### Attempt 1: Count the number of digits in each position
```java
class Solution {
    public int totalHammingDistance(int[] nums) {
        int[] digitCounts = new int[2];
        int distance = 0;

        for (int i = 0; i < 32; i++) {
            digitCounts[0] = 0;
            digitCounts[1] = 0;

            for (int j = 0; j < nums.length; j++) {
                digitCounts[nums[j] & 1]++;
                nums[j] >>>= 1;
            }

            distance += digitCounts[0] * digitCounts[1];
        }

        return distance;
    }
}
```
- Runtime: 7 ms (Beats: 63.82%)
- Memory: 45.22 MB (Beats: 26.07%)

<br>
