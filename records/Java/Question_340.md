# [LeetCode Records](../../README.md) - Question 340 Longest Substring with At Most K Distinct Characters

### Attempt 1: Use an int[] to track the character counts
```java
class Solution {
    public int lengthOfLongestSubstringKDistinct(String s, int k) {
        char[] arr = s.toCharArray();
        int maxLength = 0;
        int[] counts = new int[128];

        int startIndex = 0;
        int endIndex = 0;
        while (endIndex < arr.length) {
            counts[arr[endIndex]]++;
            endIndex++;

            if (isValid(counts, k)) {
                maxLength = Math.max(maxLength, endIndex - startIndex);
            } else {
                counts[arr[startIndex]]--;
                startIndex++;
            }
        }

        return maxLength;
    }

    private boolean isValid(int[] counts, int k) {
        int count = 0;

        for (int i = 0; i < 128; i++) {
            if (counts[i] > 0) {
                count++;

                if (count > k) {
                    return false;
                }
            }
        }

        return true;
    }
}
```
- Runtime: 13 ms (Beats: 28.42%)
- Memory: 42.23 MB (Beats: 94.63%)

<br>
