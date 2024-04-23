# [LeetCode Records](../README.md) - Question 266 Palindrome Permutation

### Attempt 1: Count the number of characters first
```java
class Solution {
    public boolean canPermutePalindrome(String s) {
        int[] saved = new int[26];
        char[] arr = s.toCharArray();

        for (char ch : arr) {
            saved[ch - 'a']++;
        }

        if (arr.length % 2 == 0) {
            for (int i : saved) {
                if (i % 2 != 0) {
                    return false;
                }
            }
        } else {
            int count = 0;
            for (int i : saved) {
                if (i % 2 != 0) {
                    count++;
                    if (count > 1) {
                        return false;
                    }
                }
            }
        }

        return true;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 41.13 MB (Beats: 59.81%)

<br>
