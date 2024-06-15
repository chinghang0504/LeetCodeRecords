# [LeetCode Records](../../README.md) - Question 2124 Check if All A's Appears Before All B's

### Attempt 1: Use two loops
```java
class Solution {
    public boolean checkString(String s) {
        char[] arr = s.toCharArray();

        int i = 0;
        while (i < arr.length) {
            if (arr[i] == 'b') {
                break;
            }

            i++;
        }
        i++;

        while (i < arr.length) {
            if (arr[i] != 'b') {
                return false;
            }

            i++;
        }

        return true;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 41.44 MB (Beats: 40.31%)

<br>
