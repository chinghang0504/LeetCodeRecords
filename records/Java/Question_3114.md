# [LeetCode Records](../../README.md) - Question 3114 Latest Time You Can Obtain After Replacing Characters

### Attempt 1: Use four if statements
```java
class Solution {
    public String findLatestTime(String s) {
        char[] arr = s.toCharArray();
        
        if (arr[0] == '?') {
            arr[0] = arr[1] == '0' || arr[1] == '1' || arr[1] == '?' ? '1' : '0';
        }

        if (arr[1] == '?') {
            arr[1] = arr[0] == '1' ? '1' : '9';
        }
        
        if (arr[3] == '?') {
            arr[3] = '5';
        }

        if (arr[4] == '?') {
            arr[4] = '9';
        }

        return new String(arr);
    }
}
```
- Runtime: 1 ms (Beats: 100.00%)
- Memory: 42.61 MB (Beats: 53.21%)

<br>
