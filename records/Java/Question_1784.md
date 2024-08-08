# [LeetCode Records](../../README.md) - Question 1784 Check if Binary String Has at Most One Segment of Ones

### Attempt 1: Use a nested loop to get the number of one segments
```java
class Solution {
    public boolean checkOnesSegment(String s) {
        char[] arr = s.toCharArray();
        int onesNum = 0;

        int i = 0;
        while (i < arr.length && onesNum < 2) {
            while (i < arr.length && arr[i] == '0') {
                i++;
            }
            if (i == arr.length) {
                break;
            }

            while (i < arr.length && arr[i] == '1') {
                i++;
            }
            onesNum++;
        }

        return onesNum == 1;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 41.63 MB (Beats: 12.50%)

<br>
