# [LeetCode Records](../../README.md) - Question 1668 Maximum Repeating Substring

### Attempt 1: Use contains() to check the repeated words
```java
class Solution {
    public int maxRepeating(String sequence, String word) {
        String target = word;
        int maxTime = sequence.length() / word.length();

        int i = 0;
        while (i < maxTime) {
            if (sequence.contains(target)) {
                target += word;
                i++;
            } else {
                break;
            }
        }

        return i;
    }
}
```
- Runtime: 1 ms (Beats: 57.52%)
- Memory: 41.66 MB (Beats: 44.54%)

<br>
