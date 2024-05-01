# [LeetCode Records](../../README.md) - Question 58 Length of Last Word

### Attempt 1: Use a signal for started
```java
class Solution {
    public int lengthOfLastWord(String s) {
        int count = 0;
        boolean started = false;

        for (int i = s.length() - 1; i >= 0; i--) {
            char ch = s.charAt(i);

            if (!started) {
                if (ch == ' ') {
                    continue;
                } else {
                    started = true;
                    count++;
                }
            } else {
                if (ch == ' ') {
                    return count;
                } else {
                    count++;
                }
            }
        }

        return count;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 41.40 MB (Beats: 77.10%)

<br>
