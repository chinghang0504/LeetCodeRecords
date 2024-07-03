# [LeetCode Records](../../README.md) - Question 2315 Count Asterisks

### Attempt 1: Use a boolean to record the pair
```java
class Solution {
    public int countAsterisks(String s) {
        boolean isOpened = false;
        int count = 0;

        for (char ch : s.toCharArray()) {
            if (ch == '|') {
                isOpened = !isOpened;
            } else if (!isOpened && ch == '*') {
                count++;
            }
        }

        return count;
    }
}
```
- Runtime: 1 ms (Beats: 100.00%)
- Memory: 41.49 MB (Beats: 51.26%)

<br>
