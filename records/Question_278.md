# [LeetCode Records](../README.md) - Question 278 First Bad Version

### Attempt 1: Loop for guessing the value
```java
public class Solution extends VersionControl {
    public int firstBadVersion(int n) {
        long start = 1, end = n;

        while (true) {
            long guess = (start + end) / 2;

            if (start == guess) {
                return isBadVersion((int)guess) ? (int)start : (int)(start + 1);
            }

            if (isBadVersion((int)guess)) {
                end = guess;
            } else {
                start = guess;
            }
        }
    }
}
```
- Runtime: 25 ms (Beats: 75.22%)
- Memory: 40.70 MB (Beats: 8.68%)

<br>
