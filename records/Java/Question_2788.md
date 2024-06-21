# [LeetCode Records](../../README.md) - Question 2788 Split Strings by Separator

### Attempt 1: Use a nested loop
```java
class Solution {
    public List<String> splitWordsBySeparator(List<String> words, char separator) {
        List<String> result = new ArrayList<>();

        for (String word : words) {
            StringBuilder stringBuilder = new StringBuilder();
            
            for (char ch : word.toCharArray()) {
                if (ch != separator) {
                    stringBuilder.append(ch);
                } else {
                    String str = stringBuilder.toString();
                    if (!str.isEmpty()) {
                        result.add(str);
                        stringBuilder = new StringBuilder();
                    }
                }
            }
            String str = stringBuilder.toString();
            if (!str.isEmpty()) {
                result.add(str);
            }
        }

        return result;
    }
}
```
- Runtime: 5 ms (Beats: 93.06%)
- Memory: 45.52 MB (Beats: 49.48%)

<br>
