# [LeetCode Records](../../README.md) - Question 2437 Number of Valid Clock Times

### Attempt 1: Check hour and minute
```java
class Solution {
    public int countTime(String time) {
        char[] arr = time.toCharArray();

        int count = 1;
        if (arr[0] == '?') {
            if (arr[1] == '?') {
                count = 24;
            } else {
                count = arr[1] >= '4' ? 2 : 3;
            }
        } else if (arr[1] == '?') {
            count = arr[0] == '2' ? 4 : 10;
        }

        if (arr[3] == '?') {
            count *= 6;
        }
        if (arr[4] == '?') {
            count *= 10;
        }
        
        return count;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 41.36 MB (Beats: 24.91%)

<br>
