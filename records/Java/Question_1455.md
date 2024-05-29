# [LeetCode Records](../../README.md) - Question 1455 Check If a Word Occurs As a Prefix of Any Word in a Sentence

### Attempt 1: Use split() to split the sentence
```java
class Solution {
    public int isPrefixOfWord(String sentence, String searchWord) {
        String[] words = sentence.split(" ");
        
        for (int i = 0; i < words.length; i++) {
            if (words[i].startsWith(searchWord)) {
                return i + 1;
            }
        }

        return -1;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 40.85 MB (Beats: 92.07%)

<br>
