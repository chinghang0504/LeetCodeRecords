# [LeetCode Records](../../README.md) - Question 2131 Longest Palindrome by Concatenating Two Letter Words

### Attempt 1: Use two HashMap to store the different character string counts and the same character string counts
```java
class Solution {
    public int longestPalindrome(String[] words) {
        Map<String, Integer> sameCharacterMap = new HashMap<>();
        Map<String, Integer> diffCharactersMap = new HashMap<>();

        int count = 0;
        for (String word : words) {
            char ch1 = word.charAt(0);
            char ch2 = word.charAt(1);
            if (ch1 != ch2) {
                String target = "" + ch2 + ch1;
                Integer targetCount = diffCharactersMap.get(target);
                if (targetCount == null || targetCount == 0) {
                    diffCharactersMap.merge(word, 1, Integer::sum);
                } else {
                    diffCharactersMap.put(target, targetCount - 1);
                    count += 4;
                }
            } else {
                Integer targetCount = sameCharacterMap.get(word);
                if (targetCount == null || targetCount == 0) {
                    sameCharacterMap.merge(word, 1, Integer::sum);
                } else if (targetCount == 1) {
                    sameCharacterMap.remove(word);
                    count += 4;
                } else {
                    sameCharacterMap.put(word, targetCount - 1);
                    count += 4;
                }
            }
        }

        return sameCharacterMap.size() > 0 ? count + 2 : count;
    }
}
```
- Runtime: 99 ms (Beats: 36.70%)
- Memory: 59.12 MB (Beats: 30.27%)

<br>
