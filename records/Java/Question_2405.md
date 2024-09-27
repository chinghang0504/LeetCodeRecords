# [LeetCode Records](../../README.md) - Question 2405 Optimal Partition of String

### Attempt 1: Use a boolean[] to record the characters in a new string
```java
class Solution {
    public int partitionString(String s) {
        boolean[] checked = new boolean[26];
        int count = 1;

        for (char ch : s.toCharArray()) {
            if (!checked[ch - 'a']) {
                checked[ch - 'a'] = true;
                continue;
            }

            count++;
            for (int i = 0; i < 26; i++) {
                checked[i] = false;
            }
            checked[ch - 'a'] = true;
        }

        return count;
    }
}
```
- Runtime: 6 ms (Beats: 95.59%)
- Memory: 45.32 MB (Beats: 49.16%)

<br>
