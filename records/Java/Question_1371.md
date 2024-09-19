# [LeetCode Records](../../README.md) - Question 1371 Find the Longest Substring Containing Vowels in Even Counts

### Attempt 1: Test from the largest substring
```java
class Solution {
    public int findTheLongestSubstring(String s) {
        char[] arr = s.toCharArray();

        for (int i = arr.length; i >= 1; i--) {
            for (int j = 0; j < arr.length - i + 1; j++) {
                if (isEvenVowelCount(arr, j, j + i)) {
                    return i;
                }
            }
        }

        return 0;
    }

    private boolean isEvenVowelCount(char[] arr, int start, int end) {
        int[] counts = new int[5];

        for (int i = start; i < end; i++) {
            if (arr[i] == 'a') {
                counts[0]++;
            } else if (arr[i] == 'e') {
                counts[1]++;
            } else if (arr[i] == 'i') {
                counts[2]++;
            } else if (arr[i] == 'o') {
                counts[3]++;
            } else if (arr[i] == 'u') {
                counts[4]++;
            }
        }
        
        for (int count : counts) {
            if (count % 2 != 0) {
                return false;
            }
        }

        return true;
    }
}
```
- Runtime: 332 ms (Beats: 5.00%)
- Memory: 47.48 MB (Beats: 23.25%)

<br>
