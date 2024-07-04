# [LeetCode Records](../../README.md) - Question 2716 Minimize String Length

### Attempt 1: Use a boolean[] to record characters
```java
class Solution {
    public int minimizedStringLength(String s) {
        boolean[] recourds = new boolean[26];

        for (char ch : s.toCharArray()) {
            recourds[ch - 'a'] = true;
        }

        int count = 0;

        for (int i = 0; i < 26; i++) {
            if (recourds[i]) {
                count++;
            }
        }

        return count;
    }
}
```
- Runtime: 3 ms (Beats: 100.00%)
- Memory: 44.50 MB (Beats: 93.16%)

<br>
