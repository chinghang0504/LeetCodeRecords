# [LeetCode Records](../../README.md) - Question 1056 Confusing Number

### Attempt 1: Check the digits and compare with the rotated number
```java
class Solution {

    private boolean[] invalidNums = { false, false, true, true, true, true, false, true, false, false };

    public boolean confusingNumber(int n) {
        int rotatedNum = 0;
        int copyNum = n;

        while (copyNum > 0) {
            rotatedNum *= 10;
            int lastDigit = copyNum % 10;
            if (invalidNums[lastDigit]) {
                return false;
            } else if (lastDigit == 6) {
                rotatedNum += 9;
            } else if (lastDigit == 9) {
                rotatedNum += 6;
            } else {
                rotatedNum += lastDigit;
            }

            copyNum /= 10;
        }

        return n != rotatedNum;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 40.24 MB (Beats: 63.23%)

<br>
