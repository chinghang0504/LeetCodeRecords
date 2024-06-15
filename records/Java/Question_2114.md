# [LeetCode Records](../../README.md) - Question 2114 Maximum Number of Words Found in Sentences

### Attempt 1: Count the number of spaces
```java
class Solution {
    public int mostWordsFound(String[] sentences) {
        int max = 0;

        for (String sentence : sentences) {
            max = Math.max(max, countWords(sentence));
        }

        return max;
    }

    private int countWords(String sentence) {
        int count = 0;

        for (char ch : sentence.toCharArray()) {
            if (ch == ' ') {
                count++;
            }
        }

        return count + 1;
    }
}
```
- Runtime: 1 ms (Beats: 100.00%)
- Memory: 42.42 MB (Beats: 81.79%)

<br>
