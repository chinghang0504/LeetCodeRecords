# [LeetCode Records](../../README.md) - Question 3099 Harshad Number

### Attempt 1: Get the sum of digits first
```java
class Solution {
    public int sumOfTheDigitsOfHarshadNumber(int x) {
        int sumOfDigits = 0;
        int num = x;

        while (num > 0) {
            sumOfDigits += num % 10;
            num /= 10;
        }

        return x % sumOfDigits == 0 ? sumOfDigits : -1;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 41.00 MB (Beats: 8.43%)

<br>
