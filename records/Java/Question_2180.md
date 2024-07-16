# [LeetCode Records](../../README.md) - Question 2180 Count Integers With Even Digit Sum

### Attempt 1: Use a helper function that tests each case
```java
class Solution {
    public int countEven(int num) {
        int count = 0;

        for (int i = 1; i <= num; i++) {
            if (isDigitSumEven(i)) {
                count++;
            }
        }

        return count;
    }

    private boolean isDigitSumEven(int num) {
        int sum = 0;
        while (num > 0) {
            sum += num % 10;
            num /= 10;
        }

        return sum % 2 == 0;
    }
}
```
- Runtime: 1 ms (Beats: 92.03%)
- Memory: 40.40 MB (Beats: 34.28%)

<br>
