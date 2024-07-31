# [LeetCode Records](../../README.md) - Question 2027 Minimum Moves to Convert String

### Attempt 1: Use a for loop to check if the character is X
```java
class Solution {
    public int minimumMoves(String s) {
        int count = 0;
        char[] arr = s.toCharArray();

        for (int i = 0; i < arr.length; ) {
            if (arr[i] == 'X') {
                count++;
                i += 3;
            } else {
                i++;
            }
        }
        
        return count;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 41.48 MB (Beats: 34.88%)

<br>
