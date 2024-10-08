# [LeetCode Records](../../README.md) - Question 1324 Print Words Vertically

### Attempt 1: Use a StringBuilder[] to store the StringBuilder
```java
class Solution {
    public List<String> printVertically(String s) {
        String[] splits = s.split("\s");
        int maxLength = 0;
        for (String word : splits) {
            maxLength = Math.max(maxLength, word.length());
        }

        StringBuilder[] stringBuilders = new StringBuilder[maxLength];
        for (int i = 0; i < maxLength; i++) {
            stringBuilders[i] = new StringBuilder();
        }

        for (String word : splits) {
            int index = 0;
            for (char ch : word.toCharArray()) {
                stringBuilders[index].append(ch);
                index++;
            }
            while (index < maxLength) {
                stringBuilders[index].append(' ');
                index++;
            }
        }

        List<String> ans = new ArrayList<>();
        for (StringBuilder stringBuilder : stringBuilders) {
            ans.add(stringBuilder.toString().stripTrailing());
        }

        return ans;
    }
}
```
- Runtime: 1 ms (Beats: 73.13%)
- Memory: 41.64 MB (Beats: 65.37%)

<br>
