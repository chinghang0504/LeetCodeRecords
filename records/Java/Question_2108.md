# [LeetCode Records](../../README.md) - Question 2108 Find First Palindromic String in the Array

### Attempt 1: Use toCharArray()
```java
class Solution {
    public String firstPalindrome(String[] words) {
        for (String str : words) {
            if (isPalindromic(str)) {
                return str;
            }
        }

        return "";
    }

    private boolean isPalindromic(String str) {
        char[] arr = str.toCharArray();

        for (int i = 0; i < arr.length / 2; i++) {
            if (arr[i] != arr[arr.length - 1 - i]) {
                return false;
            }
        }

        return true;
    }
}
```
- Runtime: 3 ms (Beats: 42.55%)
- Memory: 44.58 MB (Beats: 91.36%)

<br>

### Attempt 2: Use charAt()
```java
class Solution {
    public String firstPalindrome(String[] words) {
        for (String str : words) {
            if (isPalindromic(str)) {
                return str;
            }
        }

        return "";
    }

    private boolean isPalindromic(String str) {
        int n = str.length();

        for (int i = 0; i < n / 2; i++) {
            if (str.charAt(i) != str.charAt(n - 1 - i)) {
                return false;
            }
        }

        return true;
    }
}
```
- Runtime: 1 ms (Beats: 100.00%)
- Memory: 44.74 MB (Beats: 68.93%)

<br>
