# [LeetCode Records](../../README.md) - Question 151 Reverse Words in a String

### Attempt 1: Use split() to separate the words
```java
class Solution {
    public String reverseWords(String s) {
        String[] splits = s.split("\s");
        StringBuilder stringBuilder = new StringBuilder();

        for (int i = splits.length - 1; i >= 0; i--) {
            if (splits[i].length() != 0) {
                if (stringBuilder.length() != 0) {
                    stringBuilder.append(" ");
                }

                stringBuilder.append(splits[i]);
            }
        }

        return stringBuilder.toString();
    }
}
```
- Runtime: 5 ms (Beats: 93.22%)
- Memory: 43.38 MB (Beats: 45.66%)

<br>
