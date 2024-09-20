# [LeetCode Records](../../README.md) - Question 2186 Minimum Number of Steps to Make Two Strings Anagram II

### Attempt 1: Use two int[] to store the number of characters
```java
class Solution {
    public int minSteps(String s, String t) {
        int[] counts1 = new int[26];
        int[] counts2 = new int[26];

        for (char ch : s.toCharArray()) {
            counts1[ch - 'a']++;
        }
        for (char ch : t.toCharArray()) {
            counts2[ch - 'a']++;
        }

        int steps = 0;
        for (int i = 0; i < 26; i++) {
            steps += Math.abs(counts1[i] - counts2[i]);
        }

        return steps;
    }
}
```
- Runtime: 11 ms (Beats: 96.07%)
- Memory: 47.14 MB (Beats: 43.20%)

<br>
