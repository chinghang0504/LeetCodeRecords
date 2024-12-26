# [LeetCode Records](../../README.md) - Question 647 Palindromic Substrings

### Attempt 1: Check from each center
```java
class Solution {
    public int countSubstrings(String s) {
        char[] arr = s.toCharArray();

        int count = 0;
        for (int i = 0; i < arr.length; i++) {
            count++;

            int start = i - 1;
            int end = i + 1;
            while (isPalindromic(arr, start, end)) {
                count++;
                start--;
                end++;
            }
        }
        for (int i = 1; i < arr.length; i++) {
            int start = i - 1;
            int end = i;
            while (isPalindromic(arr, start, end)) {
                count++;
                start--;
                end++;
            }
        }

        return count;
    }

    private boolean isPalindromic(char[] arr, int start, int end) {
        if (start < 0 || end >= arr.length) {
            return false;
        }

        return arr[start] == arr[end];
    }
}
```
- Runtime: 2 ms (Beats: 99.23%)
- Memory: 41.52 MB (Beats: 63.15%)

<br>
