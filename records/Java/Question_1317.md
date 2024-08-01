# [LeetCode Records](../../README.md) - Question 1317 Convert Integer to the Sum of Two No-Zero Integers

### Attempt 1: Use a while loop to test every case
```java
class Solution {
    public int[] getNoZeroIntegers(int n) {
        int a = n - 1;
        int b = 1;

        while (true) {
            if (!containsZeros(a) && !containsZeros(b)) {
                return new int[]{ a, b };
            } else {
                a--;
                b++;
            }
        }
    }

    private boolean containsZeros(int num) {
        while (num > 0) {
            if (num % 10 == 0) {
                return true;
            }

            num /= 10;
        }

        return false;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 41.15 MB (Beats: 51.00%)

<br>
