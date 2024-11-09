# [LeetCode Records](../../README.md) - Question 1362 Closest Divisors

### Attempt 1: Use Math.sqrt() to find the divisors
```java
class Solution {
    public int[] closestDivisors(int num) {
        int[] divisors1 = getDivisors(num + 1);
        int[] divisors2 = getDivisors(num + 2);

        if (divisors1[1] - divisors1[0] <= divisors2[1] - divisors2[0]) {
            return divisors1;
        } else {
            return divisors2;
        }
    }

    private int[] getDivisors(int num) {
        int divisor = (int)Math.sqrt(num);

        for (int i = divisor; i >= 2; i--) {
            if (num % i == 0) {
                return new int[]{ i, num / i };
            }
        }

        return new int[]{ 1, num };
    }
}
```
- Runtime: 6 ms (Beats: 76.67%)
- Memory: 40.89 MB (Beats: 79.46%)

<br>
