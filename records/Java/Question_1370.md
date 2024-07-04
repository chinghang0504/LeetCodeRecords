# [LeetCode Records](../../README.md) - Question 1370 Increasing Decreasing String

### Attempt 1: Use an int[] to save the character counts
```java
class Solution {
    public String sortString(String s) {
        int[] counts = new int[26];
        char[] arr = s.toCharArray();

        for (char ch : arr) {
            counts[ch - 'a']++;
        }

        int count = 0;
        StringBuilder stringBuilder = new StringBuilder();

        while (count != arr.length) {
            for (int i = 0; i < 26; i++) {
                if (counts[i] > 0) {
                    stringBuilder.append((char)(i + 'a'));
                    counts[i]--;
                    count++;
                }
            }
            for (int i = 25; i >= 0; i--) {
                if (counts[i] > 0) {
                    stringBuilder.append((char)(i + 'a'));
                    counts[i]--;
                    count++;
                }
            }
        }

        return stringBuilder.toString();
    }
}
```
- Runtime: 2 ms (Beats: 99.85%)
- Memory: 43.06 MB (Beats: 82.67%)

<br>
