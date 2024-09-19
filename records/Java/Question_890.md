# [LeetCode Records](../../README.md) - Question 890 Find and Replace Pattern

### Attempt 1: Convert the pattern to digits
```java
class Solution {
    public List<String> findAndReplacePattern(String[] words, String pattern) {
        int[] patternDigits = convertPatternToDigits(pattern);

        List<String> ans = new ArrayList<>();
        for (String word : words) {
            int[] wordDigits = convertPatternToDigits(word);
            if (Arrays.equals(patternDigits, wordDigits)) {
                ans.add(word);
            }
        }

        return ans;
    }

    private int[] convertPatternToDigits(String pattern) {
        char[] arr = pattern.toCharArray();
        int[] digits = new int[arr.length];
        int digitIndex = 0;
        int[] letters = new int[26];
        int letterRank = 1;

        for (char ch : arr) {
            int rank = letters[ch - 'a'];
            if (rank == 0) {
                letters[ch - 'a'] = letterRank;
                rank = letterRank;
                letterRank++;
            }

            digits[digitIndex] = rank;
            digitIndex++;
        }

        return digits;
    }
}
```
- Runtime: 1 ms (Beats: 77.12%)
- Memory: 41.76 MB (Beats: 97.60%)

<br>
