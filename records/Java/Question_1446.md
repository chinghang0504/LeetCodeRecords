# [LeetCode Records](../../README.md) - Question 1446 Consecutive Characters

### Attempt 1: Record the current and the maximum counts
```java
class Solution {
    public int maxPower(String s) {
        char[] arr = s.toCharArray();
        int maxCount = 0;
        int count = 1;
        char prevCh = arr[0];

        for (int i = 1; i < arr.length; i++) {
            if (arr[i] == prevCh) {
                count++;
            } else {
                maxCount = Math.max(maxCount, count);
                count = 1;
                prevCh = arr[i];
            }
        }
        maxCount = Math.max(maxCount, count);

        return maxCount;
    }
}
```
- Runtime: 1 ms (Beats: 100.00%)
- Memory: 42.32 MB (Beats: 7.61%)

<br>
