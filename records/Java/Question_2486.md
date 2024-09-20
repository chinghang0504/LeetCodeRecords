# [LeetCode Records](../../README.md) - Question 2486 Append Characters to String to Make Subsequence

### Attempt 1: Find the first mising character in string t
```java
class Solution {
    public int appendCharacters(String s, String t) {
        char[] arr1 = s.toCharArray();
        char[] arr2 = t.toCharArray();

        int rightIndex = 0;
        for (int i = 0; i < arr1.length && rightIndex < arr2.length; i++) {
            if (arr1[i] == arr2[rightIndex]) {
                rightIndex++;
            }
        }

        return arr2.length - rightIndex;
    }
}
```
- Runtime: 3 ms (Beats: 97.68%)
- Memory: 45.08 MB (Beats: 89.51%)

<br>
