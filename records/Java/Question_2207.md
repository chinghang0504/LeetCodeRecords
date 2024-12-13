# [LeetCode Records](../../README.md) - Question 2207 Maximize Number of Subsequences in a String

### Attempt 1: Count the number of first character and the number of second character
```java
class Solution {
    public long maximumSubsequenceCount(String text, String pattern) {
        char[] arr = text.toCharArray();
        char ch1 = pattern.charAt(0);
        char ch2 = pattern.charAt(1);

        if (ch1 == ch2) {
            long count = 1;
            for (int i = 0; i < arr.length; i++) {
                if (arr[i] == ch1) {
                    count++;
                }
            }

            return count * (count - 1) / 2;
        }

        int chCount1 = 0;
        int chCount2 = 0;
        for (int i = 0; i < arr.length; i++) {
            if (arr[i] == ch1) {
                chCount1++;
            } else if (arr[i] == ch2) {
                chCount2++;
            }
        }

        int currCount = chCount2;
        long count = 0;
        for (int i = 0; i < arr.length; i++) {
            if (arr[i] == ch1) {
                count += currCount;
            } else if (arr[i] == ch2) {
                currCount--;
            }
        }

        return count + Math.max(chCount1, chCount2);
    }
}
```
- Runtime: 8 ms (Beats: 83.87%)
- Memory: 45.82 MB (Beats: 21.88%)

<br>
