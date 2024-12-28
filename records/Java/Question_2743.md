# [LeetCode Records](../../README.md) - Question 2743 Count Substrings Without Repeating Character

### Attempt 1: Use sum of integers formula
```java
class Solution {
    public int numberOfSpecialSubstrings(String s) {
        char[] arr = s.toCharArray();
        int count = 0;

        int[] charCounts = new int[26];
        int charCount = 0;
        int startIndex = 0;
        for (int i = 0; i < arr.length; i++) {
            charCounts[arr[i] - 'a']++;

            if (charCounts[arr[i] - 'a'] < 2) {
                charCount++;
            } else {
                count += (1 + charCount) * charCount / 2;
                charCount++;

                if (charCounts[arr[i] - 'a'] >= 2) {
                    while (charCounts[arr[i] - 'a'] >= 2) {
                        charCounts[arr[startIndex] - 'a']--;
                        startIndex++;
                        charCount--;
                    }

                    int deleteCount = i - startIndex;
                    count -= (1 + deleteCount) * deleteCount / 2;
                }
            }
        }
        count += (1 + charCount) * charCount / 2;

        return count;
    }
}
```
- Runtime: 23 ms (Beats: 81.55%)
- Memory: 45.66 MB (Beats: 31.07%)

<br>
