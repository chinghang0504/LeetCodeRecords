# [LeetCode Records](../../README.md) - Question 2129 Capitalize the Title

### Attempt 1: Use a loop
```java
class Solution {
    public String capitalizeTitle(String title) {
        char[] arr = title.toCharArray();
        StringBuilder stringBuilder = new StringBuilder();

        int startIndex = 0;
        int endIndex = 0;
        while (true) {
            while (endIndex < arr.length && arr[endIndex] != ' ') {
                endIndex++;
            }

            if (endIndex - startIndex <= 2) {
                for (int i = startIndex; i < endIndex; i++) {
                    stringBuilder.append(Character.toLowerCase(arr[i]));
                }
            } else {
                stringBuilder.append(Character.toUpperCase(arr[startIndex]));
                for (int i = startIndex + 1; i < endIndex; i++) {
                    stringBuilder.append(Character.toLowerCase(arr[i]));
                }
            }

            if (endIndex >= arr.length) {
                break;
            }

            stringBuilder.append(' ');
            endIndex++;
            startIndex = endIndex;
        }

        return stringBuilder.toString();
    }
}
```
- Runtime: 1 ms (Beats: 98.17%)
- Memory: 41.80 MB (Beats: 89.40%)

<br>
