# [LeetCode Records](../README.md) - Question 500 Keyboard Row

### Attempt 1: Use an int array to record the row index of keys
```java
import java.util.Arrays;

class Solution {
    public String[] findWords(String[] words) {
        int[] keyboards = { 2, 3, 3, 2, 1, 2, 2, 2, 1, 2, 2, 2, 3, 3, 1, 1, 1, 1, 2, 1, 1, 3, 1, 3, 1, 3 };

        String[] result = new String[words.length];
        int count = 0;

        for (int i = 0; i < words.length; i++) {
            char[] arr = words[i].toCharArray();
            int row = keyboards[Character.toLowerCase(arr[0]) - 'a'];
            for (int j = 1; j < arr.length; j++) {
                if (keyboards[Character.toLowerCase(arr[j]) - 'a'] != row) {
                    row = -1;
                    break;
                }
            }

            if (row != -1) {
                result[count++] = words[i];
            }
        }

        return Arrays.copyOf(result, count);
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 41.41 MB (Beats: 36.66%)

<br>
