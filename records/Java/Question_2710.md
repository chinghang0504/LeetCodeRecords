# [LeetCode Records](../../README.md) - Question 2710 Remove Trailing Zeros From a String

### Attempt 1: Find the last index that is not a zero character
```java
class Solution {
    public String removeTrailingZeros(String num) {
        char[] numArray = num.toCharArray();

        int endIndex = numArray.length;
        for (int i = endIndex - 1; i >= 0; i--) {
            if (numArray[i] == '0') {
                endIndex = i;
            } else {
                break;
            }
        }

        StringBuilder stringBuilder = new StringBuilder();
        for (int i = 0; i < endIndex; i++) {
            stringBuilder.append(numArray[i]);
        }

        return stringBuilder.toString();
    }
}
```
- Runtime: 2 ms (Beats: 40.82%)
- Memory: 45.03 MB (Beats: 15.31%)

<br>
