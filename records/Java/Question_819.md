# [LeetCode Records](../../README.md) - Question 819 Most Common Word

### Attempt 1: Use a HashSet to save the banned words and a HashMap to record the frequency of each word
```java
class Solution {
    public String mostCommonWord(String paragraph, String[] banned) {
        Set<String> bannedWords = new HashSet<>();
        for (String bannedWord : banned) {
            bannedWords.add(bannedWord);
        }

        Map<String, Integer> map = new HashMap<>();
        String[] words = paragraph.split("[ !?',;.]+");
        for (String word : words) {
            String lowerCaseWord = word.toLowerCase();
            if (!bannedWords.contains(lowerCaseWord)) {
                map.merge(word.toLowerCase(), 1, Integer::sum);
            }
        }

        return map.entrySet().stream().max(new Comparator<Map.Entry<String, Integer>>() {
            @Override
            public int compare(Map.Entry<String, Integer> o1, Map.Entry<String, Integer> o2) {
                int val1 = o1.getValue();
                int val2 = o2.getValue();
                return Integer.compare(val1, val2);
            }
        }).get().getKey();
    }
}
```
- Runtime: 12 ms (Beats: 78.66%)
- Memory: 43.30 MB (Beats: 24.12%)

<br>
