# [LeetCode Records](../../README.md) - Question 1641 Count Sorted Vowel Strings

### Attempt 1: Use an int[][] to store the previous calculated values
```java
class Solution {

    int[][] saved;

    public int countVowelStrings(int n) {
        saved = new int[n][5];
        int count = 0;

        count += countVowelStringsRecursion(n, 'a');
        count += countVowelStringsRecursion(n, 'e');
        count += countVowelStringsRecursion(n, 'i');
        count += countVowelStringsRecursion(n, 'o');
        count += countVowelStringsRecursion(n, 'u');

        return count;
    }

    private int countVowelStringsRecursion(int n, char lastCh) {
        if (n == 1) {
            return 1;
        }

        int count = 0;

        if (lastCh == 'a') {
            saved[n-1][0] = countVowelStringsRecursion(n - 1, 'a');
            saved[n-1][1] = countVowelStringsRecursion(n - 1, 'e');
            saved[n-1][2] = countVowelStringsRecursion(n - 1, 'i');
            saved[n-1][3] = countVowelStringsRecursion(n - 1, 'o');
            saved[n-1][4] = countVowelStringsRecursion(n - 1, 'u');

            count += saved[n-1][0];
            count += saved[n-1][1];
            count += saved[n-1][2];
            count += saved[n-1][3];
            count += saved[n-1][4];
        } else if (lastCh == 'e') {
            count += saved[n-1][1];
            count += saved[n-1][2];
            count += saved[n-1][3];
            count += saved[n-1][4];
        } else if (lastCh == 'i') {
            count += saved[n-1][2];
            count += saved[n-1][3];
            count += saved[n-1][4];
        } else if (lastCh == 'o') {
            count += saved[n-1][3];
            count += saved[n-1][4];
        } else if (lastCh == 'u') {
            count += saved[n-1][4];
        }

        return count;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 40.41 MB (Beats: 34.60%)

<br>
