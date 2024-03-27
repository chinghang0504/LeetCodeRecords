# [LeetCode Records](../README.md) - Question 22 Generate Parentheses

### Attempt 1: Use recursion
```java
class Solution {
    public List<String> generateParenthesis(int n) {
        List<String> result = new ArrayList<>();

        generateParenthesisRecursion(n, result, "", 0, 0);

        return result;
    }

    void generateParenthesisRecursion(int n, List<String> result, String currString, int usedOpen, int usedClosed) {
        if (usedOpen < usedClosed) {
            return ;
        } else if (usedOpen == n && usedClosed == n) {
            result.add(currString);
            return;
        }

        if (usedOpen < n) {
            generateParenthesisRecursion(n, result, currString + '(', usedOpen + 1, usedClosed);
            generateParenthesisRecursion(n, result, currString + ')', usedOpen, usedClosed + 1);
        } else {
            generateParenthesisRecursion(n, result, currString + ')', usedOpen, usedClosed + 1);
        }
    }
}
```
- Runtime: 2 ms (Beats: 52.13%)
- Memory: 43.22 MB (Beats: 38.91%)

<br>
