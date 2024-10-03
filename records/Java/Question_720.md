# [LeetCode Records](../../README.md) - Question 720 Longest Word in Dictionary

### Attempt 1: Use a HashSet to store the words
```java
class Solution {
    public String longestWord(String[] words) {
        Set<String> set = new HashSet<>();
        for (String word : words) {
            set.add(word);
        }

        Arrays.sort(words, (w1, w2) -> {
            int len1 = w1.length();
            int len2 = w2.length();
            return len1 != len2 ? len2 - len1 : w1.compareTo(w2);
        });

        for (String word : words) {
            boolean containsAll = true;
            for (int i = word.length() - 1; i >= 1; i--) {
                if (!set.contains(word.substring(0, i))) {
                    containsAll = false;
                    break;
                }
            }

            if (containsAll) {
                return word;
            }
        }

        return "";
    }
}
```
- Runtime: 12 ms (Beats: 61.51%)
- Memory: 44.07 MB (Beats: 99.16%)

<br>
