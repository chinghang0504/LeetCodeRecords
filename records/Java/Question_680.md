# [LeetCode Records](../../README.md) - Question 680 Valid Palindrome II

### Attempt 1: Use a helper function that check if the subarray is palindrome
```java
class Solution {
    public boolean validPalindrome(String s) {
        char[] arr = s.toCharArray();

        int i = 0;
        int j = arr.length - 1;
        while (i < j) {
            if (arr[i] != arr[j]) {
                return isPalindrome(arr, i + 1, j) || isPalindrome(arr, i, j - 1);
            } else {
                i++;
                j--;
            }
        }

        return true;
    }

    private boolean isPalindrome(char[] arr, int start, int end) {
        int i = start;
        int j = end;

        while (i < j) {
            if (arr[i] != arr[j]) {
                return false;
            } else {
                i++;
                j--;
            }
        }

        return true;
    }
}
```
- Runtime: 5 ms (Beats: 26.01%)
- Memory: 45.26 MB (Beats: 59.48%)

<br>
