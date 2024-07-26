# [LeetCode Records](../../README.md) - Question 2928 Distribute Candies Among Children I

### Attempt 1: Use a nested loop
```java
class Solution {
    public int distributeCandies(int n, int limit) {
        int count = 0;

        for (int i = 0; i <= limit; i++) {
            for (int j = 0; j <= limit; j++) {
                for (int k = 0; k <= limit; k++) {
                    if (i + j + k == n) {
                        count++;
                    }
                }
            }
        }

        return count;
    }
}
```
- Runtime: 15 ms (Beats: 41.45%)
- Memory: 41.24 MB (Beats: 7.95%)

<br>
