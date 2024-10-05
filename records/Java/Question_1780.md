# [LeetCode Records](../../README.md) - Question 1780 Check if Number is a Sum of Powers of Three

### Attempt 1: Use Math.log() to find the highest power
```java
class Solution {
    public boolean checkPowersOfThree(int n) {
        int power = (int)(Math.log(n) / Math.log(3));
        int currVal = (int)Math.pow(3, power);

        while (n > 0 && power >= 0) {
            if (n >= currVal) {
                n -= currVal;
            }

            power--;
            currVal /= 3;
        }

        return n == 0;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 40.85 MB (Beats: 7.84%)

<br>
