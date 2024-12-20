# [LeetCode Records](../../README.md) - Question 97 Interleaving String

### Attempt 1: Use an int[][] as a cache
```java
class Solution {

    private char[] arr1;
    private char[] arr2;
    private char[] arr3;
    private int[][] cache;
    
    public boolean isInterleave(String s1, String s2, String s3) {
        arr1 = s1.toCharArray();
        arr2 = s2.toCharArray();
        arr3 = s3.toCharArray();

        if (arr1.length + arr2.length != arr3.length) {
            return false;
        }

        cache = new int[arr1.length + 1][arr2.length + 1];

        return isInterleaveRecursion(0, 0, 0);
    }

    private boolean isInterleaveRecursion(int i, int j, int k) {
        if (k == arr3.length) {
            return true;
        } else if (cache[i][j] != 0) {
            return cache[i][j] == 1;
        }

        if (i < arr1.length && arr1[i] == arr3[k] && isInterleaveRecursion(i + 1, j, k + 1)) {
            cache[i][j] = 1;
            return true;
        }
        if (j < arr2.length && arr2[j] == arr3[k] && isInterleaveRecursion(i, j + 1, k + 1)) {
            cache[i][j] = 1;
            return true;
        }

        cache[i][j] = 2;
        return false;
    }

}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 42.16 MB (Beats: 21.69%)

<br>
