# [LeetCode Records](../../README.md) - Question 2427 Number of Common Factors

### Attempt 1: Use a loop
```java
class Solution {
    public int commonFactors(int a, int b) {
        int min = Math.min(a, b);
        int count = 0;

        for (int i = 1; i <= min; i++) {
            if (a % i == 0 && b % i == 0) {
                count++;
            }
        }

        return count;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 40.04 MB (Beats: 71.92%)

<br>
