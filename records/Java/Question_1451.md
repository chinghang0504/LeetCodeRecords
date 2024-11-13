# [LeetCode Records](../../README.md) - Question 1451 Rearrange Words in a Sentence

### Attempt 1: Use split() to get the String[]
```java
class Solution {
    public String arrangeWords(String text) {
        String[] splits = text.split("\s");
        splits[0] = splits[0].toLowerCase();

        Arrays.sort(splits, (str1, str2) -> str1.length() - str2.length());

        StringBuilder stringBuilder = new StringBuilder();
        stringBuilder.append(Character.toUpperCase(splits[0].charAt(0)));
        stringBuilder.append(splits[0].substring(1));
        for (int i = 1; i < splits.length; i++) {
            stringBuilder.append(' ');
            stringBuilder.append(splits[i]);
        }

        return stringBuilder.toString();
    }
}
```
- Runtime: 17 ms (Beats: 100.00%)
- Memory: 45.60 MB (Beats: 46.02%)

<br>
