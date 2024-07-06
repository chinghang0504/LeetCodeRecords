# [LeetCode Records](../../README.md) - Question 1935 Maximum Number of Words You Can Type

### Attempt 1: Use a HashSet to record the brokenLetters
```java
class Solution {
    public int canBeTypedWords(String text, String brokenLetters) {
        Set<Character> set = new HashSet<>();
        for (char ch : brokenLetters.toCharArray()) {
            set.add(ch);
        }

        int count = 0;
        boolean canTyped = true;

        for (char ch : text.toCharArray()) {
            if (ch != ' ') {
                if (set.contains(ch)) {
                    canTyped = false;
                }
            } else {
                if (canTyped) {
                    count++;
                } else {
                   canTyped = true; 
                }
            }
        }
        if (canTyped) {
            count++;
        }

        return count;
    }
}
```
- Runtime: 4 ms (Beats: 39.93%)
- Memory: 41.81 MB (Beats: 81.98%)

<br>
