# [LeetCode Records](../../README.md) - Question 374 Guess Number Higher or Lower

### Attempt 1: Use long to handle overflow problem
```java
public class Solution extends GuessGame {
    public int guessNumber(int n) {
        int start = 1;
        int end = n;

        while (true) {
            int middle = (int)(((long)end + start) / 2);
            int guessResult = guess(middle);

            if (guessResult == 0) {
                return middle;
            } else if (guessResult == -1) {
                end = middle - 1;
            } else {
                start = middle + 1;
            }
        }
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 40.22 MB (Beats: 46.51%)

<br>
