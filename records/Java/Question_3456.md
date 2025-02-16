# [LeetCode Records](../../README.md) - Question 3456 Find Special Substring of Length K

### Attempt 1: Check all substrings of length k which all contain the same character first
```java
class Solution {
    public boolean hasSpecialSubstring(String s, int k) {
        char[] arr = s.toCharArray();

        if (arr.length == 1) {
            return true;
        }

        for (int i = k; i <= arr.length; i++) {
            int startIndex = i - k;
            int endIndex = i;
            char ch = arr[startIndex];

            if (isAllSameCharacter(arr, ch, startIndex, endIndex)) {
                if (startIndex - 1 >= 0 && arr[startIndex - 1] == ch) {
                    continue;
                }
                if (endIndex < arr.length && arr[endIndex] == ch) {
                    continue;
                }

                return true;
            }
        }

        return false;
    }

    private boolean isAllSameCharacter(char[] arr, char ch, int startIndex, int endIndex) {
        for (int i = startIndex + 1; i < endIndex; i++) {
            if (arr[i] != ch) {
                return false;
            }
        }

        return true;
    }
}
```
- Runtime: 1 ms (Beats: 100.00%)
- Memory: 42.26 MB (Beats: 100.00%)

<br>
