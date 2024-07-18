# [LeetCode Records](../../README.md) - Question 3090 Maximum Length Substring With Two Occurrences

### Attempt 1: Use an int[] to save the character counts
```java
class Solution {
    public int maximumLengthSubstring(String s) {
        char[] arr = s.toCharArray();
        int[] counts = new int[26];
        int maxLength = 0;
        int currLength = 0;
        int startIndex = 0;

        for (char ch : arr) {
            while (counts[ch - 'a'] >= 2) {
                counts[arr[startIndex] - 'a']--;
                currLength--;
                startIndex++;
            }

            counts[ch - 'a']++;
            currLength++;
            maxLength = Math.max(maxLength, currLength);
        }

        return maxLength;
    }
}
```
- Runtime: 1 ms (Beats: 100.00%)
- Memory: 42.46 MB (Beats: 40.34%)

<br>
