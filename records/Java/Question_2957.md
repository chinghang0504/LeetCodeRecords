# [LeetCode Records](../../README.md) - Question 2957 Remove Adjacent Almost-Equal Characters

### Attempt 1: Check the adjacent characters
```java
class Solution {
    public int removeAlmostEqualCharacters(String word) {
        char[] arr = word.toCharArray();
        int count = 0;

        int i = 0;
        while (i < arr.length - 1) {
            if (Math.abs(arr[i] - arr[i + 1]) <= 1) {
                count++;
                i += 2;
            } else {
                i++;
            }
        }

        return count;
    }
}
```
- Runtime: 1 ms (Beats: 100.00%)
- Memory: 42.16 MB (Beats: 35.45%)

<br>
