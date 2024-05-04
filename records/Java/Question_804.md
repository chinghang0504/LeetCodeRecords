# [LeetCode Records](../../README.md) - Question 804 Unique Morse Code Words

### Attempt 1: Use a HashSet
```java
class Solution {
    private final String[] morseCodes = {
            ".-", "-...", "-.-.", "-..", ".",
            "..-.", "--.", "....", "..", ".---",
            "-.-", ".-..", "--", "-.", "---",
            ".--.", "--.-", ".-.", "...", "-",
            "..-", "...-", ".--", "-..-", "-.--",
            "--.."
    };

    public int uniqueMorseRepresentations(String[] words) {
        Set<String> set = new HashSet<>();

        for (String word : words) {
            StringBuilder stringBuilder = new StringBuilder();
            for (char ch : word.toCharArray()) {
                stringBuilder.append(morseCodes[ch - 'a']);
            }
            set.add(stringBuilder.toString());
        }

        return set.size();
    }
}
```
- Runtime: 2 ms (Beats: 94.93%)
- Memory: 41.56 MB (Beats: 50.42%)

<br>
