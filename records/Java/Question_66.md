# [LeetCode Records](../../README.md) - Question 66 Plus One

### Attempt 1: Start from backward and create a new array if the original array does not have enough of space
```java
class Solution {
    public int[] plusOne(int[] digits) {
        int plusOne = 1;
        
        for (int i = digits.length - 1; i >= 0; i--) {
            int sum = digits[i] + plusOne;
            if (sum >= 10) {
                plusOne = 1;
                sum -= 10;
            } else {
                plusOne = 0;
            }
            digits[i] = sum;
        }

        if (plusOne == 1) {
            int[] newDigits = new int[digits.length + 1];
            System.arraycopy(digits, 0, newDigits, 1, digits.length);
            newDigits[0] = 1;
            return newDigits;
        } else {
            return digits;
        }
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 41.82 MB (Beats: 30.26%)

<br>
