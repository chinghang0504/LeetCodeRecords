# [LeetCode Records](../../README.md) - Question 1347 Minimum Number of Steps to Make Two Strings Anagram

### Attempt 1: Use two int[] to store the character counts
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

        int count = 0;
        for (int i = 0; i < 26; i++) {
            count += Math.abs(counts2[i] - counts1[i]);
        }

        return count / 2;
    }
}
```
- Runtime: 6 ms (Beats: 99.18%)
- Memory: 44.96 MB (Beats: 94.47%)

<br>
