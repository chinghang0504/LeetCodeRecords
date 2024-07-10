# [LeetCode Records](../../README.md) - Question 2506 Count Pairs Of Similar Strings

### Attempt 1: Use boolean[] to compare
```java
class Solution {
    public int similarPairs(String[] words) {
        int count = 0;

        for (int i = 0; i < words.length - 1; i++) {
            boolean[] targetCounts = new boolean[26];
            for (char ch : words[i].toCharArray()) {
                targetCounts[ch - 'a'] = true;
            }

            for (int j = i + 1; j < words.length; j++) {
                boolean[] counts = new boolean[26];
                for (char ch : words[j].toCharArray()) {
                    counts[ch - 'a'] = true;
                }

                boolean isSimilar = true;
                for (int k = 0; k < 26; k++) {
                    if (targetCounts[k] != counts[k]) {
                        isSimilar = false;
                        break;
                    }
                }

                if (isSimilar) {
                    count++;
                }
            }
        }

        return count;
    }
}
```
- Runtime: 37 ms (Beats: 56.17%)
- Memory: 44.65 MB (Beats: 49.51%)

<br>
