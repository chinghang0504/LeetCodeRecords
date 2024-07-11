# [LeetCode Records](../../README.md) - Question 1624 Largest Substring Between Two Equal Characters

### Attempt 1: Use two int[] to store the minimum index and the maximum index of the characters
```java
class Solution {
    public int maxLengthBetweenEqualCharacters(String s) {
        int[] minIndices = new int[26];
        int[] maxIndices = new int[26];
        char[] arr = s.toCharArray();

        for (int i = 0; i < arr.length; i++) {
            int index = arr[i] - 'a';
            if (minIndices[index] == 0) {
                minIndices[index] = i + 1;
            }
        }

        for (int i = arr.length - 1; i >= 0; i--) {
            int index = arr[i] - 'a';
            if (maxIndices[index] == 0) {
                maxIndices[index] = i + 1;
            }
        }

        int max = -1;
        for (int i = 0; i < 26; i++) {
            max = Math.max(max, maxIndices[i] - minIndices[i] - 1);
        }

        return max;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 41.05 MB (Beats: 78.27%)

<br>
