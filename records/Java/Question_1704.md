# [LeetCode Records](../../README.md) - Question 1704 Determine if String Halves Are Alike

### Attempt 1: Use a helper function with a switch statement
```java
class Solution {
    public boolean halvesAreAlike(String s) {
        char[] word = s.toCharArray();
        int half = word.length / 2;
        
        return getVowelNum(word, 0, half) == getVowelNum(word, half, word.length);
    }

    private int getVowelNum(char[] word, int start, int end) {
        int count = 0;

        for (int i = start; i < end; i++) {
            switch (word[i]) {
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
                    count++;
                    break;
            }
        }

        return count;
    }
}
```
- Runtime: 1 ms (Beats: 99.49%)
- Memory: 41.87 MB (Beats: 26.36%)

<br>
