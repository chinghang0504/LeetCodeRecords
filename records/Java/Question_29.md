# [LeetCode Records](../../README.md) - Question 29 Divide Two Integers

### Attempt 1: Increase the divisor for each loop
```java
class Solution {
    public int divide(int dividend, int divisor) {
        if (dividend == 0) {
            return 0;
        }

        boolean isNegative = (dividend > 0 && divisor < 0) || (dividend < 0 && divisor > 0);
        long absDividend = Math.abs((long) dividend);
        long absDivisor = Math.abs((long) divisor);
        long absNextDivisor = absDivisor;
        long quotient = 0;
        long multiplier = 1;
        while (absDividend - absNextDivisor >= 0) {
            absDividend -= absNextDivisor;
            quotient += multiplier;

            absNextDivisor += absDivisor;
            multiplier++;
        }
        if (absDividend - absDivisor >= 0) {
            while (true) {
                if (absDividend - absNextDivisor >= 0) {
                    absDividend -= absNextDivisor;
                    quotient += multiplier;
                    break;
                } else {
                    absNextDivisor -= absDivisor;
                    multiplier--;
                }
            }
        }

        if (isNegative) {
            quotient *= -1;
        }

        if (quotient >= Integer.MAX_VALUE) {
            return Integer.MAX_VALUE;
        } else if (quotient <= Integer.MIN_VALUE) {
            return Integer.MIN_VALUE;
        } else {
            return (int) quotient;
        }
    }
}
```
- Runtime: 4 ms (Beats: 7.05%)
- Memory: 40.42 MB (Beats: 94.05%)

<br>
