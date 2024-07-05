# [LeetCode Records](../../README.md) - Question 1002 Find Common Characters

### Attempt 1: Use an int[][] to record character counts
```java
class Solution {
    public List<String> commonChars(String[] words) {
        int n = words.length;
        int[][] counts = new int[n][26];

        for (int i = 0; i < n; i++) {
            for (char ch : words[i].toCharArray()) {
                counts[i][ch - 'a']++;
            }
        }

        List<String> result = new ArrayList<>();
        for (int j = 0; j < 26; j++) {
            int min = Integer.MAX_VALUE;
            for (int i = 0; i < n; i++) {
                min = Math.min(min, counts[i][j]);
            }

            for (int i = 0; i < min; i++) {
                result.add("" + (char)(j + 'a'));
            }
        }

        return result;
    }
}
```
- Runtime: 4 ms (Beats: 42.74%)
- Memory: 42.92 MB (Beats: 63.79%)

<br>
