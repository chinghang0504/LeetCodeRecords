# [LeetCode Records](../../README.md) - Question 791 Custom Sort String

### Attempt 1: Use an int[] to store the character counts
```java
class Solution {
    public String customSortString(String order, String s) {
        int[] counts = new int[26];
        for (char ch : s.toCharArray()) {
            counts[ch - 'a']++;
        }

        StringBuilder stringBuilder = new StringBuilder();
        for (char ch : order.toCharArray()) {
            while (counts[ch - 'a'] > 0) {
                counts[ch - 'a']--;
                stringBuilder.append(ch);
            }
        }

        for (int i = 0; i < 26; i++) {
            while (counts[i] > 0) {
                counts[i]--;
                stringBuilder.append((char)(i + 'a'));
            }
        }

        return stringBuilder.toString();
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 41.92 MB (Beats: 16.59%)

<br>
