# [LeetCode Records](../../README.md) - Question 1736 Latest Time by Replacing Hidden Digits

### Attempt 1: Use multiple if statements
```java
class Solution {
    public String maximumTime(String time) {
        char[] arr = time.toCharArray();

        if (arr[0] == '?') {
            if (arr[1] == '?') {
                arr[0] = '2';
                arr[1] = '3';
            } else {
                arr[0] = arr[1] <= '3' ? '2' : '1';
            }
        } else if (arr[1] == '?') {
            arr[1] = arr[0] == '2' ? '3' : '9';
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
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 41.46 MB (Beats: 65.43%)

<br>
