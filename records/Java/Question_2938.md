# [LeetCode Records](../../README.md) - Question 2938 Separate Black and White Balls

### Attempt 1: Track the current white space
```java
class Solution {
    public long minimumSteps(String s) {
        char[] arr = s.toCharArray();
        
        long count = 0;
        int i = 0;
        while (i < arr.length && arr[i] == '0') {
            i++;
        }

        int currWhiteSpace = i;
        while (i < arr.length) {
            if (arr[i] == '0') {
                count += i - currWhiteSpace;
                currWhiteSpace++;
            }

            i++;
        }

        return count;
    }
}
```
- Runtime: 7 ms (Beats: 100.00%)
- Memory: 45.62 MB (Beats: 20.43%)

<br>
