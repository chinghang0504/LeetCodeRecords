# [LeetCode Records](../../README.md) - Question 2047 Number of Valid Words in a Sentence

### Attempt 1: Use a helper function that check if it is a valid word
```java
class Solution {
    public int countValidWords(String sentence) {
        char[] arr = sentence.toCharArray();
        int count = 0;
        
        int start = 0;
        for (int i = 0; i < arr.length; i++) {
            char ch = arr[i];
            if (ch == ' ') {
                if (arr[start] != ' ' && isValidWord(arr, start, i)) {
                    count++;
                }
                start = i;
            } else if (arr[start] == ' ') {
                start = i;
            }
        }
        if (arr[start] != ' ' && isValidWord(arr, start, arr.length)) {
            count++;
        }

        return count;
    }

    private boolean isValidWord(char[] arr, int start, int end) {
        boolean hasHypen = false;
        boolean hasPunctuation = false;
        int hypenIndex = -1;
        int punctuationIndex = -1;

        for (int i = start; i < end; i++) {
            char ch = arr[i];
            if (Character.isLowerCase(ch)) {

            } else if (isPunctuation(ch)) {
                if (hasPunctuation) {
                    return false;
                } else {
                    hasPunctuation = true;
                    punctuationIndex = i;
                }
            } else if (ch == '-') {
                if (hasHypen) {
                    return false;
                } else {
                    hasHypen = true;
                    hypenIndex = i;
                }
            } else {
                return false;
            }
        }

        if (hasHypen) {
            if (hypenIndex == start || hypenIndex == end - 1) {
                return false;
            } else if (!Character.isLowerCase(arr[hypenIndex - 1]) || !Character.isLowerCase(arr[hypenIndex + 1])) {
                return false;
            }
        }

        if (hasPunctuation) {
            if (punctuationIndex != end - 1) {
                return false;
            }
        }
        
        return true;
    }

    private boolean isPunctuation(char ch) {
        return ch == '!' || ch == '.' || ch == ',';
    }
}
```
- Runtime: 2 ms (Beats: 95.25%)
- Memory: 42.38 MB (Beats: 88.55%)

<br>
