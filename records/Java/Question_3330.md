# [LeetCode Records](../../README.md) - Question 3330 Find the Original Typed String I

### Attempt 1: Count the number of characters that are the same as the previous character
```java
class Solution {
    public int possibleStringCount(String word) {
        char[] arr = word.toCharArray();

        int count = 0;
        for (int i = 1; i < arr.length; i++) {
            if (arr[i] == arr[i - 1]) {
                count++;
            }
        }

        return count + 1;
    }
}
```
- Runtime: 1 ms (Beats: 100.00%)
- Memory: 42.36 MB (Beats: 100.00%)

<br>
