# [LeetCode Records](../../README.md) - Question 1528 Shuffle String

### Attempt 1: Use a char[] and String.valueOf()
```java
class Solution {
    public String restoreString(String s, int[] indices) {
        char[] word = s.toCharArray();
        char[] result = new char[indices.length];

        for (int i = 0; i < indices.length; i++) {
            result[indices[i]] = word[i];
        }

        return String.valueOf(result);
    }
}
```
- Runtime: 1 ms (Beats: 73.16%)
- Memory: 44.30 MB (Beats: 81.08%)

<br>
