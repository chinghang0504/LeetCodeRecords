# [LeetCode Records](../../README.md) - Question 1881 Maximum Value after Insertion

### Attempt 1: Compare each digit in the string
```java
class Solution {
    public String maxValue(String n, int x) {
        char[] arr = n.toCharArray();
        StringBuilder stringBuilder = new StringBuilder();
        char ch = (char)(x + '0');

        boolean isInserted = false;
        int i = 0;
        if (arr[0] == '-') {
            stringBuilder.append('-');
            i++;

            for (; i < arr.length; i++) {
                if (ch < arr[i]) {
                    stringBuilder.append(ch);
                    isInserted = true;
                    break;
                } else {
                    stringBuilder.append(arr[i]);
                }
            }
        } else {
            for (; i < arr.length; i++) {
                if (ch > arr[i]) {
                    stringBuilder.append(ch);
                    isInserted = true;
                    break;
                } else {
                    stringBuilder.append(arr[i]);
                }
            }
        }

        for (; i < arr.length; i++) {
            stringBuilder.append(arr[i]);
        }

        if (!isInserted) {
            stringBuilder.append(ch);
        }

        return stringBuilder.toString();
    }
}
```
- Runtime: 21 ms (Beats: 31.58%)
- Memory: 45.59 MB (Beats: 61.17%)

<br>
