# [LeetCode Records](../../README.md) - Question 1055 Shortest Way to Form String

### Attempt 1: Use two indices to track the characters on both array
```java
class Solution {
    public int shortestWay(String source, String target) {
        char[] sourceArr = source.toCharArray();
        char[] targetArr = target.toCharArray();
        int[] sourceCounts = new int[26];
        int[] targetCounts = new int[26];

        for (char ch : sourceArr) {
            sourceCounts[ch - 'a']++;
        }
        for (char ch : targetArr) {
            targetCounts[ch - 'a']++;
        }

        for (int i = 0; i < 26; i++) {
            if (targetCounts[i] != 0 && sourceCounts[i] == 0) {
                return -1;
            }
        }

        int count = 1;
        int sourceIndex = 0;
        int targetIndex = 0;
        while (targetIndex < targetArr.length) {
            if (sourceIndex == sourceArr.length) {
                sourceIndex = 0;
                count++;
            }

            if (sourceArr[sourceIndex] == targetArr[targetIndex]) {
                targetIndex++;
            }

            sourceIndex++;
        }

        return count;
    }
}
```
- Runtime: 2 ms (Beats: 99.45%)
- Memory: 41.48 MB (Beats: 65.13%)

<br>
