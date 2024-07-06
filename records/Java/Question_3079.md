# [LeetCode Records](../../README.md) - Question 3079 Find the Sum of Encrypted Integers

### Attempt 1: Use a helper function to calculate the encrypted number
```java
class Solution {
    public int sumOfEncryptedInt(int[] nums) {
        int sum = 0;

        for (int num : nums) {
            sum += encrypt(num);
        }

        return sum;
    }

    private int encrypt(int num) {
        int[] digits = new int[4];
        int size = 0;

        while (num > 0) {
            digits[size] = num % 10;
            num /= 10;
            size++;
        }

        int maxDigit = digits[0];
        for (int i = 1; i < size; i++) {
            maxDigit = Math.max(maxDigit, digits[i]);
        }

        int result = maxDigit;
        for (int i = 1; i < size; i++) {
            result = result * 10 + maxDigit;
        }

        return result;
    }
}
```
- Runtime: 1 ms (Beats: 99.89%)
- Memory: 42.91 MB (Beats: 41.31%)

<br>
