# [LeetCode Records](../../README.md) - Question 1525 Number of Good Ways to Split a String

### Attempt 1: Use int[] to store the left string and the right string character counts
```java
class Solution {

    public int numSplits(String s) {
        char[] arr = s.toCharArray();
        int count = 0;
        int[] leftCounts = new int[26];
        int[] rightCounts = new int[26];
        int leftDinstinctCount = 0;
        int rightDinstinctCount = 0;
        
        for (char ch : arr) {
            rightCounts[ch - 'a']++;
        }
        for (int i = 0; i < 26; i++) {
            if (rightCounts[i] > 0) {
                rightDinstinctCount++;
            }
        }
        
        for (char ch : arr) {
            leftCounts[ch - 'a']++;
            if (leftCounts[ch - 'a'] == 1) {
                leftDinstinctCount++;
            }

            rightCounts[ch - 'a']--;
            if (rightCounts[ch - 'a'] == 0) {
                rightDinstinctCount--;
            }

            if (leftDinstinctCount == rightDinstinctCount) {
                count++;
            }
        }

        return count;
    }
}
```
- Runtime: 4 ms (Beats: 99.81%)
- Memory: 44.36 MB (Beats: 89.51%)

<br>
