# [LeetCode Records](../../README.md) - Question 884 Uncommon Words from Two Sentences

### Attempt 1: Use a HashMap to record the word frequence
```java
class Solution {
    public String[] uncommonFromSentences(String s1, String s2) {
        Map<String, Integer> map = new HashMap<>();

        for (String word : s1.split("\\s+")) {
            map.merge(word, 1, Integer::sum);
        }
        for (String word : s2.split("\\s+")) {
            map.merge(word, 1, Integer::sum);
        }

        return map.entrySet().stream()
                .filter(x -> x.getValue() == 1)
                .map(x -> x.getKey())
                .toArray(String[]::new);
    }
}
```
- Runtime: 6 ms (Beats: 18.45%)
- Memory: 42.33 MB (Beats: 14.97%)

<br>
