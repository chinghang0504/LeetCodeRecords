# [LeetCode Records](../../README.md) - Question 3206 Alternating Groups I

### Attempt 1: Use a loop and check the groups across the end of array
```java
class Solution {
    public int numberOfAlternatingGroups(int[] colors) {
        int count = 0;

        for (int i = 0; i < colors.length - 2; i++) {
            if (colors[i] == colors[i + 2] && colors[i] != colors[i + 1]) {
                count++;
            }
        }
        if (colors[colors.length - 2] == colors[0] && colors[0] != colors[colors.length - 1]) {
            count++;
        }
        if (colors[colors.length - 1] == colors[1] && colors[1] != colors[0]) {
            count++;
        }

        return count;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 43.04 MB (Beats: 45.93%)

<br>
