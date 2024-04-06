# [LeetCode Records](../README.md) - Question 415 Add Strings

### Attempt 1: 
```java
class Solution {
    public String addStrings(String num1, String num2) {
        char[] arr1 = num1.toCharArray();
        char[] arr2 = num2.toCharArray();
        StringBuilder stringBuilder = new StringBuilder();

        int i = arr1.length - 1;
        int j = arr2.length - 1;
        int addOne = 0;
        while (i >= 0 && j >= 0) {
            int val = arr1[i--] + arr2[j--] + addOne - 96;
            if (val > 9) {
                addOne = 1;
                val -= 10;
            } else {
                addOne = 0;
            }
            stringBuilder.append(val);
        }
        while (i >= 0) {
            int val = arr1[i--] + addOne - 48;
            if (val > 9) {
                addOne = 1;
                val -= 10;
            } else {
                addOne = 0;
            }
            stringBuilder.append(val);
        }
        while (j >= 0) {
            int val = arr2[j--] + addOne - 48;
            if (val > 9) {
                addOne = 1;
                val -= 10;
            } else {
                addOne = 0;
            }
            stringBuilder.append(val);
        }
        if (addOne == 1) {
            stringBuilder.append('1');
        }

        return stringBuilder.reverse().toString();
    }
}
```
- Runtime: 1 ms (Beats: 100.00%)
- Memory: 42.61 MB (Beats: 50.11%)

<br>
