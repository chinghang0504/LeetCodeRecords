# [LeetCode Records](../../README.md) - Question 2303 Calculate Amount Paid in Taxes

### Attempt 1: Use a loop
```java
class Solution {
    public double calculateTax(int[][] brackets, int income) {
        double tax = 0.0;
        
        int calculated = 0;
        int remainder = income;
        int i = 0;
        while (true) {
            int range = brackets[i][0] - calculated;
            if (remainder > range) {
                calculated += range;
                remainder -= range;
                tax += range * brackets[i][1] / 100.0;
                i++;
            } else {
                tax += remainder * brackets[i][1] / 100.0;
                return tax;
            }
        }
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 44.61 MB (Beats: 37.54%)

<br>
