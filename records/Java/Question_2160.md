# [LeetCode Records](../../README.md) - Question 2160 Minimum Sum of Four Digit Number After Splitting Digits

### Attempt 1: Use Arrays.sort()
```java
class Solution {
    public int minimumSum(int num) {
        int[] digits = new int[4];
        for (int i = 0; i < 4; i++) {
            digits[i] = num % 10;
            num /= 10;
        }

        Arrays.sort(digits);

        int num1 = digits[0] * 10 + digits[2];
        int num2 = digits[1] * 10 + digits[3];
        return num1 + num2;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 40.43 MB (Beats: 29.38%)

<br>
