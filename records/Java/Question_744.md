# [LeetCode Records](../../README.md) - Question 744 Find Smallest Letter Greater Than Target

### Attempt 1: 
```java
class Solution {
    public char nextGreatestLetter(char[] letters, char target) {
        for (char letter : letters) {
            if (letter > target) {
                return letter;
            }
        }

        return letters[0];
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 44.43 MB (Beats: 24.13%)

<br>
