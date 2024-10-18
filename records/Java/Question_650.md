# [LeetCode Records](../../README.md) - Question 650 2 Keys Keyboard

### Attempt 1: Find all the factors of n
```java
class Solution {
    public int minSteps(int n) {
        int sum = 0;
        int factor = 2;
        while (n > 1) {
            if (n % factor == 0) {
                sum += factor;
                n /= factor;
            } else {
                factor++;
            }
        }

        return sum;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 40.20 MB (Beats: 87.15%)

<br>
