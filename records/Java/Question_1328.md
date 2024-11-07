# [LeetCode Records](../../README.md) - Question 1328 Break a Palindrome

### Attempt 1: Check the first character that is not 'a'
```java
class Solution {
    public String breakPalindrome(String palindrome) {
        char[] arr = palindrome.toCharArray();

        if (arr.length == 1) {
            return "";
        }

        boolean isAllSame = true;
        for (int i = 0; i < arr.length / 2; i++) {
            if (arr[i] != 'a') {
                arr[i] = 'a';
                isAllSame = false;
                break;
            }
        }
        if (isAllSame) {
            arr[arr.length - 1] = 'b';
        }

        return new String(arr);
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 41.27 MB (Beats: 81.08%)

<br>
