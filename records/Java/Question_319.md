# [LeetCode Records](../../README.md) - Question 319 Bulb Switcher

### Attempt 1: Find the pattern first
```java
class Solution {
    public int bulbSwitch(int n) {
        int count = 0;
        int factor = 3;
        while (n > 0) {
            n -= factor;
            factor += 2;
            count++;
        }

        return count;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 40.10 MB (Beats: 71.92%)

<br>
