# [LeetCode Records](../../README.md) - Question 2380 Time Needed to Rearrange a Binary String

### Attempt 1: Execute until there is no change
```java
class Solution {
    public int secondsToRemoveOccurrences(String s) {
        char[] arr = s.toCharArray();

        int count = 0;
        while (true) {
            boolean isChanged = false;

            for (int i = 1; i < arr.length;) {
                if (arr[i - 1] == '0' && arr[i] == '1') {
                    arr[i - 1] = '1';
                    arr[i] = '0';
                    i += 2;
                    isChanged = true;
                } else {
                    i++;
                }
            }

            if (!isChanged) {
                return count;
            }
            
            count++;
        }
    }
}
```
- Runtime: 24 ms (Beats: 66.27%)
- Memory: 41.62 MB (Beats: 76.12%)

<br>
