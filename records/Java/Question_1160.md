# [LeetCode Records](../../README.md) - Question 1160 Find Words That Can Be Formed by Characters

### Attempt 1: Use int[] to save the character counts
```java
class Solution {
    public int countCharacters(String[] words, String chars) {
        int[] targetCounts = new int[26];

        for (char ch : chars.toCharArray()) {
            targetCounts[ch - 'a']++;
        }

        int count = 0;
        for (String word : words) {
            int[] counts = new int[26];
            for (char ch : word.toCharArray()) {
                counts[ch - 'a']++;
            }

            boolean isGood = true;
            for (int i = 0; i < 26; i++) {
                if (counts[i] > targetCounts[i]) {
                    isGood = false;
                    break;
                }
            }

            if (isGood) {
                count += word.length();
            }
        }

        return count;
    }
}
```
- Runtime: 5 ms (Beats: 90.29%)
- Memory: 44.84 MB (Beats: 83.08%)

<br>
