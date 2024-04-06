# [LeetCode Records](../README.md) - Question 389 Find the Difference

### Attempt 1: Use two int arrays to record counts
```java
class Solution {
    public char findTheDifference(String s, String t) {
        int[] saved1 = new int[26];
        int size1 = s.length();
        for (int i = 0; i < size1; i++) {
            saved1[s.charAt(i) - 'a']++;
        }

        int[] saved2 = new int[26];
        int size2 = t.length();
        for (int i = 0; i < size2; i++) {
            saved2[t.charAt(i) - 'a']++;
        }

        for (int i = 0; i < 26; i++) {
            if (saved1[i] != saved2[i]) {
                return (char)('a' + i);
            }
        }

        return 0;
    }
}
```
- Runtime: 2 ms (Beats: 68.45%)
- Memory: 42.15 MB (Beats: 7.69%)

<br>
