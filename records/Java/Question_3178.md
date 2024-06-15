# [LeetCode Records](../../README.md) - Question 3178 Find the Child Who Has the Ball After K Seconds

### Attempt 1: Use mathematic formula
```java
class Solution {
    public int numberOfChild(int n, int k) {
        k = k % ((n - 1) * 2);

        return k < n ? k : 2 * n - k - 2;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 40.51 MB (Beats: 77.22%)

<br>
