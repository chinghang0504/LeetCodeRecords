# [LeetCode Records](../../README.md) - Question 1748 Sum of Unique Elements

### Attempt 1: Use an int[]
```java
class Solution {
    public int sumOfUnique(int[] nums) {
        int[] counts = new int[101];

        for (int num : nums) {
            counts[num]++;
        }

        int sum = 0;
        for (int i = 1; i < 101; i++) {
            if (counts[i] == 1) {
                sum += i;
            }
        }

        return sum;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 41.18 MB (Beats: 43.52%)

<br>
