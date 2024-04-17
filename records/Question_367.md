# [LeetCode Records](../README.md) - Question 367 Valid Perfect Square

### Attempt 1: Loop for guessing the range
```java
class Solution {
    public boolean isPerfectSquare(int num) {
        if (num == 0 || num == 1) {
            return true;
        }

        long start = 0, end = num;

        while (true) {
            long guess = (start + end) / 2;
            long square = guess * guess;

            if (guess == start) {
                return false;
            }

            if (square == num) {
                return true;
            } else if (square > num) {
                end = guess;
            } else {
                start = guess;
            }
        }
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 40.01 MB (Beats: 76.39%)

<br>
