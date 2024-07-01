# [LeetCode Records](../../README.md) - Question 1374 Generate a String With Characters That Have Odd Counts

### Attempt 1: Use StringBuilder
```java
class Solution {
    public String generateTheString(int n) {
        StringBuilder stringBuilder = new StringBuilder();

        if (n % 2 == 0) {
            for (int i = 0; i < n - 1; i++) {
                stringBuilder.append('a');
            }
            stringBuilder.append('b');
        } else {
            for (int i = 0; i < n; i++) {
                stringBuilder.append('a');
            }
        }

        return stringBuilder.toString();
    }
}
```
- Runtime: 1 ms (Beats: 85.83%)
- Memory: 41.17 MB (Beats: 38.54%)

<br>
