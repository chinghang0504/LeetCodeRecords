# [LeetCode Records](../../README.md) - Question 3300 Minimum Element After Replacement With Digit Sum

### Attempt 1: Test every case
```java
class Solution {
    public int minElement(int[] nums) {
        int min = Integer.MAX_VALUE;

        for (int num : nums) {
            int sum = 0;

            while (num > 0) {
                sum += num % 10;
                num /= 10;
            }
            
            min = Math.min(min, sum);
        }

        return min;
    }
}
```
- Runtime: 1 ms (Beats: 100.00%)
- Memory: 42.85 MB (Beats: 100.00%)

<br>
