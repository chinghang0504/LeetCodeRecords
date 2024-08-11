# [LeetCode Records](../../README.md) - Question 1332 Remove Palindromic Subsequences

### Attempt 1: Use a helper function to check if it is palindromic
```java
class Solution {
    public int removePalindromeSub(String s) {
        return isPalindromic(s) ? 1 : 2;
    }

    private boolean isPalindromic(String str) {
        char[] arr = str.toCharArray();

        for (int i = 0; i < arr.length / 2; i++) {
            if (arr[i] != arr[arr.length - i - 1]) {
                return false;
            }
        }

        return true;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 41.60 MB (Beats: 12.44%)

<br>
