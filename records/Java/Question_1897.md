# [LeetCode Records](../../README.md) - Question 1897 Redistribute Characters to Make All Strings Equal

### Attempt 1: Use an int[] to save the character counts
```java
class Solution {
    public boolean makeEqual(String[] words) {
        int n = words.length;
        int[] counts = new int[26];

        for (String word : words) {
            for (char ch : word.toCharArray()) {
                counts[ch - 'a']++;
            }
        }

        for (int i = 0; i < 26; i++) {
            if (counts[i] % n != 0) {
                return false;
            }
        }

        return true;
    }
}
```
- Runtime: 2 ms (Beats: 95.21%)
- Memory: 43.87 MB (Beats: 50.98%)

<br>
