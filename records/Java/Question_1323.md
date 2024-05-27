# [LeetCode Records](../../README.md) - Question 1323 Maximum 69 Number

### Attempt 1: Use an int[] to save the digits
```java
class Solution {
    public int maximum69Number (int num) {
        int[] digits = new int[4];

        int count = 0;
        while (num > 0) {
            digits[count] = num % 10;
            count++;
            num /= 10;
        }

        for (int i = count - 1; i >= 0; i--) {
            if (digits[i] == 6) {
                digits[i] = 9;
                break;
            }
        }

        int result = 0;
        for (int i = count - 1; i >= 0; i--) {
            result *= 10;
            result += digits[i];
        }

        return result;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 39.69 MB (Beats: 99.31%)

<br>
