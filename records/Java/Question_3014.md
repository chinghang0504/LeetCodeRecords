# [LeetCode Records](../../README.md) - Question 3014 Minimum Number of Pushes to Type Word I

### Attempt 1: Compare the size
```java
class Solution {
    public int minimumPushes(String word) {
        int size = word.length();

        if (size <= 8) {
            return size;
        } else if (size <= 16) {
            return 8 + (size - 8) * 2;
        } else if (size <= 24) {
            return 24 + (size - 16) * 3;
        } else {
            return 48 + (size - 24) * 4; 
        }
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 41.56 MB (Beats: 76.87%)

<br>
