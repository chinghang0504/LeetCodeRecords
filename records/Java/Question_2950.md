# [LeetCode Records](../../README.md) - Question 2950 Number of Divisible Substrings

### Attempt 1: Use recursion to calculate the next sum
```java
class Solution {

    private int[] scores = { 1, 1, 2, 2, 2, 3, 3, 3, 4, 4, 4, 5, 5, 5, 6, 6, 6, 7, 7, 7, 8, 8, 8, 9, 9, 9 };
    private int count;

    public int countDivisibleSubstrings(String word) {
        char[] arr = word.toCharArray();
        count = 0;

        for (int i = 0; i < arr.length; i++) {
            countDivisibleSubstringsRecursion(arr, i, 0, 0);
        }

        return count;
    }

    private void countDivisibleSubstringsRecursion(char[] arr, int index, int sum, int len) {
        if (index >= arr.length) {
            return;
        }

        int nextSum = sum + scores[arr[index] - 'a'];
        int nextLen = len + 1;
        if (nextSum % nextLen == 0) {
            count++;
        }

        countDivisibleSubstringsRecursion(arr, index + 1, nextSum, nextLen);
    }
}
```
- Runtime: 137 ms (Beats: 29.60%)
- Memory: 42.83 MB (Beats: 70.40%)

<br>
