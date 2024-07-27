# [LeetCode Records](../../README.md) - Question 3136 Valid Word

### Attempt 1: Use a helper function that gets the types of characters
```java
class Solution {
    public boolean isValid(String word) {
        char[] arr = word.toCharArray();
        boolean hasVowel = false;
        boolean hasConsonant = false;

        if (arr.length < 3) {
            return false;
        }

        for (char ch : arr) {
            int type = getType(ch);

            if (type == 0) {
                return false;
            } else if (type == 2) {
                hasVowel = true;
            } else if (type == 3) {
                hasConsonant = true;
            }

        }

        return hasVowel && hasConsonant;
    }

    private int getType(char ch) {
        if (ch >= '0' && ch <= '9') {
            return 1;
        }

        char lower = Character.toLowerCase(ch);
        if (lower == 'a' || lower == 'e' || lower == 'i' || lower == 'o' || lower == 'u') {
            return 2;
        }

        if ((ch >= 'A' && ch <= 'Z') || (ch >= 'a' && ch <= 'z')) {
            return 3;
        }

        return 0;
    }
}
```
- Runtime: 1 ms (Beats: 99.32%)
- Memory: 41.70 MB (Beats: 85.54%)

<br>
