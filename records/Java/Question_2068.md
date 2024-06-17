# [LeetCode Records](../../README.md) - Question 2068 Check Whether Two Strings are Almost Equivalent

### Attempt 1: Use two int[]
```java
class Solution {
    public boolean checkAlmostEquivalent(String word1, String word2) {
        int[] count1 = new int[26];
        int[] count2 = new int[26];

        for (char ch : word1.toCharArray()) {
            count1[ch - 'a']++;
        }
        for (char ch : word2.toCharArray()) {
            count2[ch - 'a']++;
        }

        for (int i = 0; i < 26; i++) {
            int diff = count2[i] - count1[i];
            if (diff < -3 || diff > 3) {
                return false;
            }
        }

        return true;
    }
}
```
- Runtime: 1 ms (Beats: 63.91%)
- Memory: 41.61 MB (Beats: 46.30%)

<br>
