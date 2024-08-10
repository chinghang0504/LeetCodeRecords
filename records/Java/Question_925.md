# [LeetCode Records](../../README.md) - Question 925 Long Pressed Name

### Attempt 1: Use two variables to save the current indices of the arrays
```java
class Solution {
    public boolean isLongPressedName(String name, String typed) {
        char[] arr1 = name.toCharArray();
        char[] arr2 = typed.toCharArray();

        if (arr1[0] != arr2[0]) {
            return false;
        } else if (arr2.length < arr1.length) {
            return false;
        }

        int index1 = 1;
        int index2 = 1;
        while (index1 < arr1.length && index2 < arr2.length) {
            if (arr1[index1] == arr2[index2]) {
                index1++;
                index2++;
            } else {
                if (arr1[index1 - 1] == arr2[index2]) {
                    index2++;
                } else {
                    return false;
                }
            }
        }

        if (index1 != arr1.length) {
            return false;
        }

        char lastCh = arr2[index2 - 1];
        while (index2 < arr2.length) {
            if (arr2[index2] != lastCh) {
                return false;
            }
            index2++;
        }

        return true;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 41.58 MB (Beats: 28.06%)

<br>
