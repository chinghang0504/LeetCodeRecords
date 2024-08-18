# [LeetCode Records](../../README.md) - Question 3258 Count Substrings That Satisfy K-Constraint I

### Attempt 1: Use a helper function to check if it is a valid substring
```java
class Solution {
    public int countKConstraintSubstrings(String s, int k) {
        char[] arr = s.toCharArray();
        int count = 0;

        for (int i = arr.length; i >= 1; i--) {
            for (int j = 0; j < arr.length - i + 1; j++) {
                if (isValidSubstring(arr, k, j, j + i)) {
                    count++;
                }
            }
        }

        return count;
    }

    private boolean isValidSubstring(char[] arr, int k, int start, int end) {
        int zeroCount = 0;
        int oneCount = 0;
        
        for (int i = start; i < end; i++) {
            if (arr[i] == '0') {
                zeroCount++;
            } else {
                oneCount++;
            }
        }

        return zeroCount <= k || oneCount <= k;
    }    
}
```
- Runtime: 13 ms (Beats: 100.00%)
- Memory: 41.99 MB (Beats: 100.00%)

<br>
