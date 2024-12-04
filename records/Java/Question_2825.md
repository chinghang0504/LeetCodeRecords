# [LeetCode Records](../../README.md) - Question 2825 Make String a Subsequence Using Cyclic Increments

### Attempt 1: Use two integers to track the current indices of the arrays
```java
class Solution {
    public boolean canMakeSubsequence(String str1, String str2) {
        char[] arr1 = str1.toCharArray();
        char[] arr2 = str2.toCharArray();

        int index1 = 0;
        int index2 = 0;
        while (index1 < arr1.length && index2 < arr2.length) {
            if (arr1[index1] == arr2[index2] || (arr1[index1] - 'a' + 1) % 26 == arr2[index2] - 'a') {
                index1++;
                index2++;
            } else {
                index1++;
            }
        }

        return index2 == arr2.length;
    }
}
```
- Runtime: 5 ms (Beats: 100.00%)
- Memory: 45.64 MB (Beats: 37.58%)

<br>
