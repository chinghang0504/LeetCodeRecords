# [LeetCode Records](../../README.md) - Question 1941 Check if All Characters Have Equal Number of Occurrences

### Attempt 1: Use an int[] to save the character counts
```java
class Solution {
    public boolean areOccurrencesEqual(String s) {
        int[] counts = new int[26];

        for (char ch : s.toCharArray()) {
            counts[ch - 'a']++;
        }

        int freq = 0;
        int i = 0;
        while (i < 26) {
            if (counts[i] != 0) {
                freq = counts[i];
                break;
            }
            i++;
        }
        while (i < 26) {
            if (counts[i] != 0 && counts[i] != freq) {
                return false;
            }
            i++;
        }

        return true;
    }
}
```
- Runtime: 1 ms (Beats: 100.00%)
- Memory: 41.72 MB (Beats: 62.55%)

<br>
