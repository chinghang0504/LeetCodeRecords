# [LeetCode Records](../../README.md) - Question 2139 Minimum Moves to Reach Target Score

### Attempt 1: Check the target that is odd or even
```java
class Solution {
    public int minMoves(int target, int maxDoubles) {
        int count = 0;

        while (target > 0 && maxDoubles > 0) {
            if (target % 2 == 1) {
                target--;
            } else {
                target /= 2;
                maxDoubles--;
            }

            count++;
        }

        return count + target - 1;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 40.10 MB (Beats: 93.69%)

<br>
