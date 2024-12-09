# [LeetCode Records](../../README.md) - Question 1400 Construct K Palindrome Strings

### Attempt 1: Count the number of single characters and the number of pair characters
```java
class Solution {
    public boolean canConstruct(String s, int k) {
        int[] counts = new int[26];
        for (char ch : s.toCharArray()) {
            counts[ch - 'a']++;
        }

        int pairCount = 0;
        int singleCount = 0;
        for (int i = 0; i < 26; i++) {
            pairCount += counts[i] / 2;
            singleCount += counts[i] % 2;
        }

        if (singleCount > k) {
            return false;
        } else if (singleCount + pairCount * 2 < k) {
            return false;
        } else {
            return true;
        }
    }
}
```
- Runtime: 4 ms (Beats: 94.19%)
- Memory: 44.79 MB (Beats: 97.90%)

<br>
