# [LeetCode Records](../../README.md) - Question 941 Valid Mountain Array

### Attempt 1: Use two while loops
```java
class Solution {
    public boolean validMountainArray(int[] arr) {
        if (arr.length < 3) {
            return false;
        }

        int i = 1;
        while (i < arr.length) {
            if (arr[i] > arr[i - 1]) {
                i++;
            } else if (arr[i] == arr[i - 1]) {
                return false;
            } else {
                break;
            }
        }

        if (i == 1) {
            return false;
        }

        i++;
        while (i < arr.length) {
            if (arr[i] < arr[i - 1]) {
                i++;
            } else if (arr[i] == arr[i - 1]) {
                return false;
            } else {
                break;
            }
        }

        return i == arr.length;
    }
}
```
- Runtime: 1 ms (Beats: 100.00%)
- Memory: 44.97 MB (Beats: 82.31%)

<br>
