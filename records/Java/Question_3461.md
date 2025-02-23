# [LeetCode Records](../../README.md) - Question 3461 Check If Digits Are Equal in String After Operations I

### Attempt 1: Use an int[] to simulate the process
```java
class Solution {
    public boolean hasSameDigits(String s) {
        char[] arr = s.toCharArray();
        int[] digits = new int[arr.length];
        for (int i = 0; i < arr.length; i++) {
            digits[i] = arr[i] - '0';
        }

        for (int size = arr.length; size > 2; size--) {
            for (int i = 1; i < size; i++) {
                digits[i - 1] = (digits[i - 1] + digits[i]) % 10;
            }
        }

        return digits[0] == digits[1];
    }
}
```
- Runtime: 1 ms (Beats: 100.00%)
- Memory: 42.18 MB (Beats: 100.00%)

<br>
