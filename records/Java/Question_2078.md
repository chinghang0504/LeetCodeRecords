# [LeetCode Records](../../README.md) - Question 2078 Two Furthest Houses With Different Colors

### Attempt 1: Use a nested loop to test every case
```java
class Solution {
    public int maxDistance(int[] colors) {
        for (int i = colors.length; i >= 1; i--) {
            for (int j = 0; j < colors.length - i + 1; j++) {
                if (colors[j] != colors[j + i - 1]) {
                    return i - 1;
                }
            }
        }

        return 1;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 41.30 MB (Beats: 70.71%)

<br>
