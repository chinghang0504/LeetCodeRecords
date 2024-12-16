# [LeetCode Records](../../README.md) - Question 2734 Lexicographically Smallest String After Substring Operation

### Attempt 1: Start from the character which is not an 'a'
```java
class Solution {
    public String smallestString(String s) {
        char[] arr = s.toCharArray();

        boolean isSelected = false;
        for (int i = 0; i < arr.length; i++) {
            if (arr[i] != 'a') {
                arr[i]--;
                for (int j = i + 1; j < arr.length && arr[j] != 'a'; j++) {
                    arr[j]--;
                }

                isSelected = true;
                break;
            }
        }

        if (!isSelected) {
            arr[arr.length - 1] = 'z';
        }

        return new String(arr);
    }
}
```
- Runtime: 11 ms (Beats: 88.72%)
- Memory: 48.40 MB (Beats: 94.47%)

<br>
