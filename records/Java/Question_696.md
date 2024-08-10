# [LeetCode Records](../../README.md) - Question 696 Count Binary Substrings

### Attempt 1: Count start from 01 or 10
```java
class Solution {
    public int countBinarySubstrings(String s) {
        char[] arr = s.toCharArray();
        int count = 0;

        for (int i = 0; i < arr.length - 1; i++) {
            count += getCounts(arr, i);
        }

        return count;
    }

    private int getCounts(char[] arr, int start) {
        int count = 0;

        int i = start;
        int j = start + 1;
        if (arr[i] == '0') {
            while (i >= 0 && j < arr.length && arr[i] == '0' && arr[j] == '1') {
                count++;
                i--;
                j++;
            }
        } else {
            while (i >= 0 && j < arr.length && arr[i] == '1' && arr[j] == '0') {
                count++;
                i--;
                j++;
            }
        }

        return count;
    }
}
```
- Runtime: 9 ms (Beats: 90.90%)
- Memory: 44.87 MB (Beats: 88.31%)

<br>
