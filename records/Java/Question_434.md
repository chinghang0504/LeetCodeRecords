# [LeetCode Records](../../README.md) - Question 434 Number of Segments in a String

### Attempt 1: 
```java
class Solution {
    public int countSegments(String s) {
        int count = 0;
        boolean isSpace = true;

        char arr[] = s.toCharArray();
        for (int i = 0; i < arr.length; i++) {
            char ch = arr[i];
            if (isSpace) {
                if (arr[i] != ' ') {
                    isSpace = false;
                    count++;
                }
            } else if (arr[i] == ' ') {
                isSpace = true;
            }
        }

        return count;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 41.28 MB (Beats: 39.78%)

<br>
