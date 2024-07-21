# [LeetCode Records](../../README.md) - Question 2287 Rearrange Characters to Make Target String

### Attempt 1: Use two int[] to save character counts
```java
class Solution {
    public int rearrangeCharacters(String s, String target) {
        int[] targetCounts = new int[26];
        for (char ch : target.toCharArray()) {
            targetCounts[ch - 'a']++;
        }

        int[] stringCounts = new int[26];
        for (char ch : s.toCharArray()) {
            stringCounts[ch - 'a']++;
        }

        int min = Integer.MAX_VALUE;
        for (int i = 0; i < 26; i++) {
            if (targetCounts[i] != 0) {
                min = Math.min(min, stringCounts[i] / targetCounts[i]);
            }
        }

        return min;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 41.47 MB (Beats: 42.74%)

<br>
