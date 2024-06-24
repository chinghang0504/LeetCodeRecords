# [LeetCode Records](../../README.md) - Question 2481 Minimum Cuts to Divide a Circle

### Attempt 1: Check if it is even
```java
class Solution {
    public int numberOfCuts(int n) {
        if (n == 1) {
            return 0;
        }
        
        return n % 2 == 0 ? n / 2 : n;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 40.20 MB (Beats: 63.14%)

<br>
