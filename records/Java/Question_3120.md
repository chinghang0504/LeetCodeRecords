# [LeetCode Records](../../README.md) - Question 3120 Count the Number of Special Characters I

### Attempt 1: Use two boolean[]
```java
class Solution {
    public int numberOfSpecialChars(String word) {
        boolean[] lowers = new boolean[26];
        boolean[] uppers = new boolean[26];

        for (char ch : word.toCharArray()) {
            if (ch <= 'Z') {
                uppers[ch - 'A'] = true;
            } else {
                lowers[ch - 'a'] = true;
            }
        }

        int count = 0;
        for (int i = 0; i < 26; i++) {
            if (lowers[i] && uppers[i]) {
                count++;
            }
        }

        return count;
    }
}
```
- Runtime: 1 ms (Beats: 100.00%)
- Memory: 42.04 MB (Beats: 82.00%)

<br>
