# [LeetCode Records](../../README.md) - Question 748 Shortest Completing Word

### Attempt 1: Use an int[] to save the character counts
```java
class Solution {
    public String shortestCompletingWord(String licensePlate, String[] words) {
        char[] arr = licensePlate.toCharArray();
        int[] counts = new int[26];

        for (char ch : arr) {
            if (ch >= 'a' && ch <= 'z') {
                counts[ch - 'a']++;
            } else if (ch >= 'A' && ch <= 'Z') {
                counts[ch - 'A']++;
            }
        }

        int minLength = Integer.MAX_VALUE;
        int minIndex = 0;
        for (int i = 0; i < words.length; i++) {
            int length = words[i].length();
            if (length < minLength && isCompleted(words[i], counts)) {
                minLength = length;
                minIndex = i;
            }
        }

        return words[minIndex];
    }

    private boolean isCompleted(String word, int[] targetCounts) {
        char[] arr = word.toCharArray();
        int[] counts = new int[26];

        for (char ch : arr) {
            counts[ch - 'a']++;
        }

        for (int i = 0; i < 26; i++) {
            if (counts[i] < targetCounts[i]) {
                return false;
            }
        }

        return true;
    }
}
```
- Runtime: 2 ms (Beats: 98.15%)
- Memory: 44.66 MB (Beats: 54.48%)

<br>
