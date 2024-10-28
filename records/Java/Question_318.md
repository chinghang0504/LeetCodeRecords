# [LeetCode Records](../../README.md) - Question 318 Maximum Product of Word Lengths

### Attempt 1: Compare every case
```java
class Solution {
    public int maxProduct(String[] words) {
        int max = 0;

        boolean[][] characters = new boolean[words.length][26];
        for (int i = 0; i < words.length; i++) {
            for (char ch : words[i].toCharArray()) {
                characters[i][ch - 'a'] = true;
            }
        }

        for (int i = 0; i < words.length - 1; i++) {
            for (int j = i + 1; j < words.length; j++) {
                if (hasNoCommonLetter(characters[i], characters[j])) {
                    max = Math.max(max, words[i].length() * words[j].length());
                }
            }
        }

        return max;
    }

    private boolean hasNoCommonLetter(boolean[] arr1, boolean[] arr2) {
        for (int i = 0; i < 26; i++) {
            if (arr1[i] && arr2[i]) {
                return false;
            }
        }

        return true;
    }
}
```
- Runtime: 34 ms (Beats: 31.08%)
- Memory: 45.58 MB (Beats: 84.06%)

<br>
