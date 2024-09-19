# [LeetCode Records](../../README.md) - Question 2330 Valid Palindrome IV

### Attempt 1: Count the number of different characters
```java
class Solution {
    public boolean makePalindrome(String s) {
        char[] arr = s.toCharArray();
        int count = 0;

        for (int i = 0; i < arr.length / 2; i++) {
            if (arr[i] != arr[arr.length - i - 1]) {
                count++;
            }
        }

        return count <= 2;
    }
}
```
- Runtime: 2 ms (Beats: 95.85%)
- Memory: 44.04 MB (Beats: 95.60%)

<br>
