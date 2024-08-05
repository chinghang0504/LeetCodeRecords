# [LeetCode Records](../../README.md) - Question 1933 Check if String Is Decomposable Into Value-Equal Substrings

### Attempt 1: Use helper functions to check if the characters in the array are same
```java
class Solution {
    public boolean isDecomposable(String s) {
        char[] arr = s.toCharArray();
        boolean twoLengthUsed = false;

        int i = 0;
        while (i + 3 < arr.length) {
            if (isTreeCharactersEqual(arr, i)) {
                i += 3;
            } else if (isTwoCharactersEqual(arr, i)) {
                if (twoLengthUsed) {
                    return false;
                } else {
                    twoLengthUsed = true;
                    i += 2;
                }
            } else {
                return false;
            }
        }

        int remainingLength = arr.length - i;
        if (remainingLength == 2) {
            return twoLengthUsed ? false : isTwoCharactersEqual(arr, i);
        } else if (remainingLength == 1) {
            return false;
        }

        return isTreeCharactersEqual(arr, i) ? twoLengthUsed : false;
    }

    private boolean isTreeCharactersEqual(char[] arr, int start) {
        return arr[start] == arr[start + 1] && arr[start] == arr[start + 2];
    }

    private boolean isTwoCharactersEqual(char[] arr, int start) {
        return arr[start] == arr[start + 1];
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 41.78 MB (Beats: 25.00%)

<br>
