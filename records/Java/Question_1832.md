# [LeetCode Records](../../README.md) - Question 1832 Check if the Sentence Is Pangram

### Attempt 1: Use boolean[] to count characters
```java
class Solution {
    public boolean checkIfPangram(String sentence) {
        boolean[] counts = new boolean[26];

        for (char ch : sentence.toCharArray()) {
            counts[ch - 'a'] = true;
        }

        for (boolean count : counts) {
            if (!count) {
                return false;
            }
        }

        return true;
    }
}
```
- Runtime: 1 ms (Beats: 88.04%)
- Memory: 41.22 MB (Beats: 82.71%)

<br>
