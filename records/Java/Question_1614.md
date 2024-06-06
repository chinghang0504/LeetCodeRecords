# [LeetCode Records](../../README.md) - Question 1614 Maximum Nesting Depth of the Parentheses

### Attempt 1: Use two variables
```java
class Solution {
    public int maxDepth(String s) {
        int max = 0;
        int curr = 0;

        for (char ch : s.toCharArray()) {
            if (ch == '(') {
                curr++;
                max = Math.max(curr, max);
            } else if (ch == ')') {
                curr--;
            }
        }

        return max;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 41.98 MB (Beats: 6.76%)

<br>
