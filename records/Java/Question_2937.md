# [LeetCode Records](../../README.md) - Question 2937 Make Three Strings Equal

### Attempt 1: Check from the leftmost characters
```java
class Solution {
    public int findMinimumOperations(String s1, String s2, String s3) {
        char[] arr1 = s1.toCharArray();
        char[] arr2 = s2.toCharArray();
        char[] arr3 = s3.toCharArray();

        if (arr1[0] != arr2[0] || arr1[0] != arr3[0]) {
            return -1;
        }

        int minSize = Math.min(Math.min(arr1.length, arr2.length), arr3.length);
        int i = 1;
        for (; i < minSize; i++) {
            if (arr1[i] != arr2[i] || arr1[i] != arr3[i]) {
                break;
            }
        }

        return arr1.length + arr2.length + arr3.length - 3 * i;
    }
}
```
- Runtime: 1 ms (Beats: 100.00%)
- Memory: 44.83 MB (Beats: 15.62%)

<br>
