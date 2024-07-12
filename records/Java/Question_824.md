# [LeetCode Records](../../README.md) - Question 824 Goat Latin

### Attempt 1: Use two helper functions, StringBuilder, and a loop
```java
class Solution {
    public String toGoatLatin(String sentence) {
        StringBuilder stringBuilder = new StringBuilder();
        int count = 1;
        boolean isFirstCh = true;
        char firstCh = 0;

        for (char ch : sentence.toCharArray()) {
            if (ch == ' ') {
                appendLastCharacters(stringBuilder, count, firstCh);
                stringBuilder.append(' ');
                count++;
                isFirstCh = true;
            } else {
                if (isFirstCh) {
                    firstCh = ch;
                    isFirstCh = false;
                    if (isVowel(ch)) {
                        stringBuilder.append(ch);
                    }
                } else {
                    stringBuilder.append(ch);
                }
            }
        }
        appendLastCharacters(stringBuilder, count, firstCh);

        return stringBuilder.toString();
    }

    private void appendLastCharacters(StringBuilder stringBuilder, int times, char firstCh) {
        if (!isVowel(firstCh)) {
            stringBuilder.append(firstCh);
        }

        stringBuilder.append('m').append('a');

        for (int i = 0; i < times; i++) {
            stringBuilder.append('a');
        }
    }

    private boolean isVowel(char ch) {
        switch (ch) {
            case 'a':
            case 'e':
            case 'i':
            case 'o':
            case 'u':
            case 'A':
            case 'E':
            case 'I':
            case 'O':
            case 'U':
                return true;
            default:
                return false;
        }
    }
}
```
- Runtime: 1 ms (Beats: 100.00%)
- Memory: 41.44 MB (Beats: 91.35%)

<br>
