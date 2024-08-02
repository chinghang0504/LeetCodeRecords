# [LeetCode Records](../../README.md) - Question 1576 Replace All ?'s to Avoid Consecutive Repeating Characters

### Attempt 1: Use a helper function that gets the next character
```java
class Solution {
    public String modifyString(String s) {
        char[] arr = s.toCharArray();

        if (arr.length == 1) {
            return "a";
        }

        if (arr[0] == '?') {
            arr[0] = getNoRepeatedChar('z', arr[1]);
        }

        for (int i = 1; i < arr.length - 1; i++) {
            if (arr[i] == '?') {
                arr[i] = getNoRepeatedChar(arr[i - 1], arr[i + 1]);
            }
        }

        if (arr[arr.length - 1] == '?') {
            arr[arr.length - 1] = getNoRepeatedChar(arr[arr.length - 2], 'z');
        }

        return new String(arr);
    }

    private char getNoRepeatedChar(char prev, char next) {
        for (char ch = 'a'; ch <= 'z'; ch++) {
            if (ch != prev && ch != next) {
                return ch;
            }
        }

        return 0;
    }
}
```
- Runtime: 1 ms (Beats: 100.00%)
- Memory: 42.30 MB (Beats: 74.47%)

<br>
