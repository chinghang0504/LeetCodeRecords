# [LeetCode Records](../../README.md) - Question 1876 Substrings of Size Three with Distinct Characters

### Attempt 1: Use a helper function to test each substring
```java
class Solution {
    public int countGoodSubstrings(String s) {
        int count = 0;
        char[] arr = s.toCharArray();

        for (int i = 2; i < arr.length; i++) {
            if (isGoodSubstring(arr[i - 2], arr[i - 1], arr[i])) {
                count++;
            }
        }

        return count;
    }

    private boolean isGoodSubstring(char ch1, char ch2, char ch3) {
        return ch1 != ch2 && ch2 != ch3 && ch1 != ch3;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 41.37 MB (Beats: 70.26%)

<br>
