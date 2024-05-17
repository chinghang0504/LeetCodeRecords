# [LeetCode Records](../../README.md) - Question 1051 Height Checker

### Attempt 1: Use .clone() and Arrays.sort()
```java
class Solution {
    public int heightChecker(int[] heights) {
        int[] expected = heights.clone();
        Arrays.sort(expected);
        
        int count = 0;
        for (int i = 0; i < heights.length; i++) {
            if (expected[i] != heights[i]) {
                count++;
            }
        }
        
        return count;
    }
}
```
- Runtime: 2 ms (Beats: 90.02%)
- Memory: 41.52 MB (Beats: 21.08%)

<br>
