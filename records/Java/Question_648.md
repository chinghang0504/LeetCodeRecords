# [LeetCode Records](../../README.md) - Question 648 Replace Words

### Attempt 1: Use startsWith() to check every word in dictionary
```java
class Solution {
    public String replaceWords(List<String> dictionary, String sentence) {
        dictionary.sort(String::compareTo);

        StringBuilder stringBuilder = new StringBuilder();
        String[] words = sentence.split("\s");
        for (int i = 0; i < words.length; i++) {
            boolean isInDictionary = true;
            String word = words[i];
            for (String wordInDictionary : dictionary) {
                if (word.startsWith(wordInDictionary)) {
                    stringBuilder.append(wordInDictionary);
                    isInDictionary = false;
                    break;
                }
            }

            if (isInDictionary) {
                stringBuilder.append(word);
            }

            stringBuilder.append(' ');
        }

        return stringBuilder.substring(0, stringBuilder.length() - 1);
    }
}
```
- Runtime: 45 ms (Beats: 51.05%)
- Memory: 55.43 MB (Beats: 42.05%)

<br>
