# [LeetCode Records](../../README.md) - Question 357 Count Numbers with Unique Digits

### Attempt 1: Use recursion
```java
class Solution {
    public int countNumbersWithUniqueDigits(int n) {
        if (n == 0) {
            return 1;
        } else if (n == 1) {
            return 10;
        }

        int sum = 9;
        for (int i = 0; i < n - 1; i++) {
            sum *= (9 - i);
        }
        return sum + countNumbersWithUniqueDigits(n - 1);
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 40.24 MB (Beats: 45.86%)

<br>
