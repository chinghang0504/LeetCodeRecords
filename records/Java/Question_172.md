# [LeetCode Records](../../README.md) - Question 172 Factorial Trailing Zeroes

### Attempt 1: Count factor of 5
```java
class Solution {
    public int trailingZeroes(int n) {
        int count = 0;
        int base = 5;

        while (base <= n) {
            count += n / base;
            base *= 5;
        }

        return count;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 40.88 MB (Beats: 25.06%)

<br>
