# [LeetCode Records](../README.md) - Question 5 Longest Palindromic Substring

### Attempt 1: Find the two- and three-character Palindromes first
```java
class Solution {
    int maxStart = 0;
    int maxEnd = 0;
    int maxLength = 0;

    public String longestPalindrome(String s) {
        for (int i = 0; i < s.length() - 1; i++) {
            char ch1 = s.charAt(i);
            char ch2 = s.charAt(i+1);

            if (ch1 == ch2) {
                extendPalindrome(s, i-1, i+2);
            }
        }

        for (int i = 0; i < s.length() - 2; i++) {
            char ch1 = s.charAt(i);
            char ch2 = s.charAt(i+2);
            if (ch1 == ch2) {
                extendPalindrome(s, i-1, i+3);
            }
        }

        if (maxLength != 0) {
            return s.substring(maxStart, maxEnd + 1);
        } else if (s.length() >= 1) {
            return s.substring(0, 1);
        } else {
            return "";
        }
    }

    private void extendPalindrome(String s, int start, int end) {
        for (; start >= 0 && end < s.length(); start--, end++) {
            if (s.charAt(start) != s.charAt(end)) {
                break;
            }
        }
        
        int length = end - start - 1;
        if (length > maxLength) {
            maxLength = length;
            maxStart = start + 1;
            maxEnd = end - 1;
        }
    }
}
```
- Runtime: 15 ms (Beats: 87.45%)
- Memory: 42.37 MB (Beats: 73.78%)

<br>
