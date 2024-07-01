# [LeetCode Records](../../README.md) - Question 2351 First Letter to Appear Twice

### Attempt 1: Use an int[] to save the character counts
```java
class Solution {
    public char repeatedCharacter(String s) {
        int[] counts = new int[26];

        for (char ch : s.toCharArray()) {
            counts[ch - 'a']++;

            if (counts[ch - 'a'] == 2) {
                return ch;
            }
        }

        return 0;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 40.94 MB (Beats: 96.49%)

<br>
