# [LeetCode Records](../../README.md) - Question 1134 Armstrong Number

### Attempt 1: Use an int[] to save the digits and Math.pow()
```java
class Solution {
    public boolean isArmstrong(int n) {
        int[] digits = new int[9];
        int size = 0;

        int copy = n;
        while (copy > 0) {
            digits[size] = copy % 10;
            size++;
            copy /= 10;
        }

        int sum = 0;
        for (int i = 0; i < size; i++) {
            sum += Math.pow(digits[i], size);
        }

        return n == sum;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 40.90 MB (Beats: 9.09%)

<br>
