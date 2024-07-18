# [LeetCode Records](../../README.md) - Question 1137 N-th Tribonacci Number

### Attempt 1: Use an int[] to save the previous values
```java
class Solution {
    public int tribonacci(int n) {
        if (n == 0) {
            return 0;
        } else if (n == 1 || n == 2) {
            return 1;
        }

        int[] saved = new int[n + 1];
        saved[0] = 0;
        saved[1] = 1;
        saved[2] = 1;
        for (int i = 3; i <= n; i++) {
            saved[i] = saved[i - 3] + saved[i - 2] + saved[i - 1];
        }

        return saved[n];
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 40.44 MB (Beats: 19.94%)

<br>
