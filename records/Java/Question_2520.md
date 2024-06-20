# [LeetCode Records](../../README.md) - Question 2520 Count the Digits That Divide a Number

### Attempt 1: Use a loop
```java
class Solution {
    public int countDigits(int num) {
        int n = num;
        int count = 0;

        while (n > 0) {
            if (num % (n % 10) == 0) {
                count++;
            }
            n /= 10;
        }

        return count;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 40.41 MB (Beats: 19.09%)

<br>
