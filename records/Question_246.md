# [LeetCode Records](../README.md) - Question 246 Strobogrammatic Number

### Attempt 1: Check from the left and the right characters
```java
class Solution {
    public boolean isStrobogrammatic(String num) {
        char[] arr = num.toCharArray();

        for (int i = 0; i < arr.length / 2; i++) {
            char ch1 = arr[i];
            char ch2 = arr[arr.length - 1 - i];

            if (ch1 == '6' && ch2 == '9') {
                continue;
            } else if (ch1 == '9' && ch2 == '6') {
                continue;
            } else if ((ch1 == '0' || ch1 == '1' || ch1 == '8') && (ch2 == '0' || ch2 == '1' || ch2 == '8')) {
                if (ch1 != ch2) {
                    return false;
                }
            } else {
                return false;
            }
        }

        if (arr.length % 2 == 1) {
            char ch = arr[arr.length / 2];
            if (ch != '0' && ch != '1' && ch != '8') {
                return false;
            }
        }

        return true;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 40.84 MB (Beats: 90.58%)

<br>
