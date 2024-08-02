# [LeetCode Records](../../README.md) - Question 2609 Find the Longest Balanced Substring of a Binary String

### Attempt 1: Use a nested loop that test every case
```java
class Solution {
    public int findTheLongestBalancedSubstring(String s) {
        char[] arr = s.toCharArray();

        for (int i = arr.length; i >= 1; i--) {
            for (int j = 0; j < arr.length - i + 1; j++) {
                if (isBalancedSubarray(arr, j, j + i)) {
                    return i;
                }
            }
        }

        return 0;
    }

    private boolean isBalancedSubarray(char[] arr, int start, int end) {
        int zeroCount = 0;
        int oneCount = 0;

        int i = start;
        for (; i < end; i++) {
            if (arr[i] == '0') {
                zeroCount++;
            } else {
                break;
            }
        }

        for (; i < end; i++) {
            if (arr[i] == '1') {
                oneCount++;
            } else {
                return false;
            }
        }

        return zeroCount == oneCount;
    }
}
```
- Runtime: 4 ms (Beats: 23.10%)
- Memory: 43.01 MB (Beats: 38.89%)

<br>
