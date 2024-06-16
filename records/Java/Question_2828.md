# [LeetCode Records](../../README.md) - Question 2828 Check if a String Is an Acronym of Words

### Attempt 1: 
```java
class Solution {
    public boolean isAcronym(List<String> words, String s) {
        char[] arr = s.toCharArray();

        if (words.size() != arr.length) {
            return false;
        }

        int i = 0;
        for (String word : words) {
            if (word.charAt(0) != arr[i]) {
                return false;
            }
            i++;
        }

        return true;
    }
}
```
- Runtime: 2 ms (Beats: 44.23%)
- Memory: 44.52 MB (Beats: 42.31%)

<br>
