# [LeetCode Records](../../README.md) - Question 2109 Adding Spaces to a String

### Attempt 1: Use StringBuilder to store the characters
```java
class Solution {
    public String addSpaces(String s, int[] spaces) {
        char[] arr = s.toCharArray();
        StringBuilder stringBuilder = new StringBuilder();
        
        int spaceIndex = 0;
        for (int i = 0; i < arr.length; i++) {
            if (spaceIndex < spaces.length && i == spaces[spaceIndex]) {
                stringBuilder.append(' ');
                spaceIndex++;
            }

            stringBuilder.append(arr[i]);
        }

        return stringBuilder.toString();
    }
}
```
- Runtime: 20 ms (Beats: 81.41%)
- Memory: 80.37 MB (Beats: 74.86%)

<br>
