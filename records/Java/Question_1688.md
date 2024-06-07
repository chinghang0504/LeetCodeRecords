# [LeetCode Records](../../README.md) - Question 1688 Count of Matches in Tournament

### Attempt 1: Use recursion
```java
class Solution {
    public int numberOfMatches(int n) {
        if (n == 1) {
            return 0;
        } else if (n == 2) {
            return 1;
        }

        if (n % 2 == 0) {
            return n / 2 + numberOfMatches(n / 2);
        } else {
            return (n - 1) / 2 + numberOfMatches((n - 1) / 2 + 1);
        }
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 40.20 MB (Beats: 54.85%)

<br>
