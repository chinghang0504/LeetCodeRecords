# [LeetCode Records](../../README.md) - Question 2544 Alternating Digit Sum

### Attempt 1: Use an int[] to save the digits
```java
class Solution {
    public int alternateDigitSum(int n) {
        int[] digits = new int[10];
        int size = 0;

        while (n > 0) {
            digits[size] = n % 10;
            n /= 10;
            size++;
        }
        
        int sum = 0;
        int factor = 1;
        for (int i = size - 1; i >= 0; i--) {
            sum += digits[i] * factor;
            factor *= -1;
        }

        return sum;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 40.14 MB (Beats: 64.64%)

<br>
