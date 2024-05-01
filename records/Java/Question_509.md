# [LeetCode Records](../../README.md) - Question 509 Fibonacci Number

### Attempt 1: Return [F(n - 1) + F(n - 2), F(n - 1)]
```java
class Solution {
    public int fib(int n) {
        return n == 0 ? 0 : fibRecursion(n)[0];
    }

    private int[] fibRecursion(int n) {
        if (n == 1) {
            return new int[]{ 1, 0 };
        }

        int[] prevResult = fibRecursion(n - 1);
        return new int[]{ prevResult[0] + prevResult[1], prevResult[0] };
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 40.83 MB (Beats: 5.68%)

<br>
