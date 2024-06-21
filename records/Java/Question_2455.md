# [LeetCode Records](../../README.md) - Question 2455 Average Value of Even Numbers That Are Divisible by Three

### Attempt 1: Use a loop
```java
class Solution {
    public int averageValue(int[] nums) {
        int sum = 0;
        int count = 0;

        for (int num : nums) {
            if (num % 6 == 0) {
                sum += num;
                count++;
            }
        }

        return count == 0 ? 0 : sum / count;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 43.94 MB (Beats: 74.02%)

<br>
