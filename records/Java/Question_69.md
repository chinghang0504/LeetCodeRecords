# [LeetCode Records](../../README.md) - Question 69 Sqrt(x)

### Attempt 1: Use divided by 2 to guess
```java
class Solution {
    public int mySqrt(int x) {
        return mySqrtRecursion(x, 0, x);
    }

    private int mySqrtRecursion(int x, int start, int end) {
        if (start + 1 >= end) {
            try {
                int squareValue = Math.multiplyExact(end, end);
                return squareValue <= x ? end : start;
            } catch (ArithmeticException e) {
                return start;
            }
        }

        int middle = (start + end) / 2;
        int squareValue;
        try {
            squareValue = Math.multiplyExact(middle, middle);
        } catch (ArithmeticException e) {
            return mySqrtRecursion(x, start, middle);
        }

        if (squareValue == x) {
            return middle;
        } else if (squareValue < x) {
            return mySqrtRecursion(x, middle, end);
        } else {
            return mySqrtRecursion(x, start, middle);
        }
    }
}
```
- Runtime: 13 ms (Beats: 12.37%)
- Memory: 44.17 MB (Beats: 7.41%)

<br>

### Attempt 2: Use n = (n + x / n) / 2 to guess
```java
class Solution {
    public int mySqrt(int x) {
        long n = x;

        while (n * n > x) {
            n = (n + x / n) / 2;
        }

        return (int) n;
    }
}
```
- Runtime: 1 ms (Beats: 85.74%)
- Memory: 41.11 MB (Beats: 12.91%)

<br>
