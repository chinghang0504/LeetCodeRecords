# [LeetCode Records](../../README.md) - Question 2586 Count the Number of Vowel Strings in Range

### Attempt 1: Use a loop
```java
class Solution {
    public int vowelStrings(String[] words, int left, int right) {
        int count = 0;

        for (int i = left; i <= right; i++) {
            String word = words[i];
            Character firstCh = word.charAt(0);
            Character lastCh = word.charAt(word.length() - 1);
            if ((firstCh == 'a' || firstCh == 'e' || firstCh == 'i' || firstCh == 'o' || firstCh == 'u') && 
            (lastCh == 'a' || lastCh == 'e' || lastCh == 'i' || lastCh == 'o' || lastCh == 'u')) {
                count++;
            }
        }

        return count;
    }
}
```
- Runtime: 1 ms (Beats: 100.00%)
- Memory: 44.60 MB (Beats: 10.14%)

<br>
