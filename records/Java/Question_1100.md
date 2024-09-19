# [LeetCode Records](../../README.md) - Question 1100 Find K-Length Substrings With No Repeated Characters

### Attempt 1: Use an int[] to store the number of characters
```java
class Solution {
    public int numKLenSubstrNoRepeats(String s, int k) {
        char[] arr = s.toCharArray();
        if (k > arr.length) {
            return 0;
        }

        int[] counts = new int[26];
        int count = 0;

        for (int i = 0; i < k; i++) {
            counts[arr[i] - 'a']++;
        }
        if (isValid(counts)) {
            count++;
        }

        for (int i = 1; i < arr.length - k + 1; i++) {
            counts[arr[i - 1] - 'a']--;
            counts[arr[i + k - 1] - 'a']++;
            if (isValid(counts)) {
                count++;
            }
        }
        
        return count;
    }

    private boolean isValid(int[] counts) {
        for (int count : counts) {
            if (count > 1) {
                return false;
            }
        }

        return true;
    }
}
```
- Runtime: 4 ms (Beats: 98.02%)
- Memory: 41.63 MB (Beats: 81.42%)

<br>
