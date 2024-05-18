# [LeetCode Records](../../README.md) - Question 1064 Fixed Point

### Attempt 1: Use linear search
```java
class Solution {
    public int fixedPoint(int[] arr) {
        for (int i = 0; i < arr.length; i++) {
            if (arr[i] == i) {
                return i;
            }
        }

        return -1;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 43.90 MB (Beats: 75.76%)

<br>
