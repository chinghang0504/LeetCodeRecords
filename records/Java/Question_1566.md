# [LeetCode Records](../../README.md) - Question 1566 Detect Pattern of Length M Repeated K or More Times

### Attempt 1: Use a helper function to count the number of patterns
```java
class Solution {
    public boolean containsPattern(int[] arr, int m, int k) {
        for (int i = 0; i < arr.length - m + 1; i++) {
            if (countPattern(arr, m, i, i + m) >= k) {
                return true;
            }
        }

        return false;
    }

    private int countPattern(int[] arr, int m, int start, int end) {
        int maxCount = 0;
        int count = 0;
        
        int i = 0;
        while (i < arr.length - m + 1) {
            boolean isPattern = true;

            for (int j = start, index = i; j < end; j++, index++) {
                if (arr[index] != arr[j]) {
                    isPattern = false;
                    break;
                }
            }

            if (isPattern) {
                count++;
                maxCount = Math.max(maxCount, count);
                i += m;
            } else {
                i++;
                count = 0;
            }
        }

        return maxCount;
    }
}
```
- Runtime: 1 ms (Beats: 30.00%)
- Memory: 41.17 MB (Beats: 59.29%)

<br>
