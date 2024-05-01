# [LeetCode Records](../../README.md) - Question 520 Detect Capital

### Attempt 1: Check the first character first
```java
class Solution {
    public boolean detectCapitalUse(String word) {
        char[] arr = word.toCharArray();

        if (arr.length == 1) {
            return true;
        }

        if (arr[0] <= 'Z' && arr[1] <= 'Z') {
            for (int i = 2; i < arr.length; i++) {
                if (arr[i] > 'Z') {
                    return false;
                }
            }
        } else {
            for (int i = 1; i < arr.length; i++) {
                if (arr[i] <= 'Z') {
                    return false;
                }
            }
        }

        return true;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 41.92 MB (Beats: 19.06%)

<br>
