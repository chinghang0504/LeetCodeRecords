# [LeetCode Records](../README.md) - Question 50 Pow(x, n)

### Attempt 1: 
```java
class Solution {
    public double myPow(double x, int n) {
        if (x == 1.0 || n == 0) {
            return 1.0;
        }

        double result = 1;
        double multiplier = x;
        long weight = 1;

        long count = 0;
        if (n > 0) {
            while (count + weight < n) {
                result *= multiplier;
                count += weight;

                multiplier *= x;
                weight++;
            }

            while (count + weight != n) {
                multiplier /= x;
                weight--;
            }

            return result * multiplier;
        } else {
            while (count - weight > n) {
                result /= multiplier;
                count -= weight;

                multiplier *= x;
                weight++;
            }

            while (count - weight != n) {
                multiplier /= x;
                weight--;
            }

            return result / multiplier;
        }
    }
}
```
- Runtime: 5 ms (Beats: 100.00%)
- Memory: 41.52 MB (Beats: 90.07%)

<br>
