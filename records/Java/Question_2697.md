# [LeetCode Records](../../README.md) - Question 2697 Lexicographically Smallest Palindrome

### Attempt 1: Compare the head and the tail
```java
class Solution {
    public String makeSmallestPalindrome(String s) {
        char[] arr = new char[s.length()];
        int size = 0;

        for (char ch : s.toCharArray()) {
            arr[size] = ch;
            size++;
        }

        for (int i = 0; i < size; i++) {
            char firshCh = arr[i];
            char lastCh = arr[size - 1 - i];
            char ch = firshCh <= lastCh ? firshCh : lastCh;
            arr[i] = ch;
            arr[size - 1 - i] = ch;
        }
        
        return new String(arr);
    }
}
```
- Runtime: 7 ms (Beats: 60.12%)
- Memory: 45.46 MB (Beats: 20.09%)

<br>
