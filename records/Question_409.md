# [LeetCode Records](../README.md) - Question 409 Longest Palindrome

### Attempt 1: Use an int array to record character counts
```java
class Solution {
    public int longestPalindrome(String s) {
        int[] saved = new int[128];
        char[] arr = s.toCharArray();

        for (int i = 0; i < arr.length; i++) {
            saved[arr[i]]++;
        }

        int count = 0;
        boolean hasOne = false;
        for (char ch = 'A'; ch <= 'Z'; ch++) {
            if (saved[ch] >= 2) {
                if (saved[ch] % 2 == 0) {
                    count += saved[ch];
                } else {
                    count += saved[ch] - 1;
                    hasOne = true;
                }
            } else if (saved[ch] == 1) {
                hasOne = true;
            }
        }
        for (char ch = 'a'; ch <= 'z'; ch++) {
            if (saved[ch] >= 2) {
                if (saved[ch] % 2 == 0) {
                    count += saved[ch];
                } else {
                    count += saved[ch] - 1;
                    hasOne = true;
                }
            } else if (saved[ch] == 1) {
                hasOne = true;
            }
        }

        return hasOne ? count + 1 : count;
    }
}
```
- Runtime: 1 ms (Beats: 100.00%)
- Memory: 41.56 MB (Beats: 74.57%)

<br>
