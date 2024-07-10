# [LeetCode Records](../../README.md) - Question 1598 Crawler Log Folder

### Attempt 1: Use a loop
```java
class Solution {
    public int minOperations(String[] logs) {
        int count = 0;

        for (String log : logs) {
            if (log.equals("../")) {
                if (count > 0) {
                    count--;
                }
            } else if (!log.equals("./")) {
                count++;
            }
        }

        return count;
    }
}
```
- Runtime: 1 ms (Beats: 99.42%)
- Memory: 41.90 MB (Beats: 51.62%)

<br>
