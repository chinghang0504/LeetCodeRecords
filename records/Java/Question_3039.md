# [LeetCode Records](../../README.md) - Question 3039 Apply Operations to Make String Empty

### Attempt 1: Find the maximum of count of characters
```java
class Solution {
    public String lastNonEmptyString(String s) {
        char[] arr = s.toCharArray();

        int[] counts = new int[26];
        for (char ch : arr) {
            counts[ch - 'a']++;
        }

        int maxCount = 0;
        for (int count : counts) {
            maxCount = Math.max(maxCount, count);
        }

        StringBuilder stringBuilder = new StringBuilder();
        for (int i = arr.length - 1; i >= 0; i--) {
            if (counts[arr[i] - 'a'] == maxCount) {
                stringBuilder.append(arr[i]);
                counts[arr[i] - 'a']--;
            }
        }

        return stringBuilder.reverse().toString();
    }
}
```
- Runtime: 14 ms (Beats: 97.44%)
- Memory: 48.52 MB (Beats: 86.49%)

<br>
