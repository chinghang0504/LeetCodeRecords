# [LeetCode Records](../../README.md) - Question 3043 Find the Length of the Longest Common Prefix

### Attempt 1: Use a HashSet to store the prefix numbers
```java
class Solution {
    public int longestCommonPrefix(int[] arr1, int[] arr2) {
        Set<Integer> set = new HashSet<>();
        for (int num : arr2) {
            while (num > 0) {
                set.add(num);
                num /= 10;
            }
        }

        int maxLen = 0;
        for (int num : arr1) {
            while (num > 0) {
                if (set.contains(num)) {
                    maxLen = Math.max(maxLen, getLength(num));
                }
                num /= 10;
            }
        }

        return maxLen;
    }

    private int getLength(int num) {
        int len = 0;
        while (num > 0) {
            len++;
            num /= 10;
        }
        return len;
    }
}
```
- Runtime: 69 ms (Beats: 43.12%)
- Memory: 55.59 MB (Beats: 68.45%)

<br>
