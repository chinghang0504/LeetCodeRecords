# [LeetCode Records](../README.md) - Question 17 Letter Combinations of a Phone Number

### Attempt 1: Use recursion
```java
class Solution {
    char[][] dict = {
            { 'a', 'b', 'c' },
            { 'd', 'e', 'f' },
            { 'g', 'h', 'i' },
            { 'j', 'k', 'l' },
            { 'm', 'n', 'o' },
            { 'p', 'q', 'r', 's' },
            { 't', 'u', 'v' },
            { 'w', 'x', 'y', 'z' }
    };


    public List<String> letterCombinations(String digits) {
        List<String> result = new ArrayList<>();

        if (!digits.isEmpty()) {
            letterCombinationsRecursion(digits, result, "", 0);
        }

        return result;
    }

    void letterCombinationsRecursion(String digits, List<String> result, String currString, int currIndex) {
        if (currIndex >= digits.length()) {
            result.add(currString);
            return;
        }

        char digit = digits.charAt(currIndex);
        char[] charArray = digitToCharArray(digit);
        for (int i = 0; i < charArray.length; i++) {
            letterCombinationsRecursion(digits, result, currString + charArray[i], currIndex + 1);
        }
    }

    char[] digitToCharArray(char digit) {
        return switch (digit) {
            case '2' -> dict[0];
            case '3' -> dict[1];
            case '4' -> dict[2];
            case '5' -> dict[3];
            case '6' -> dict[4];
            case '7' -> dict[5];
            case '8' -> dict[6];
            case '9' -> dict[7];
            default -> null;
        };
    }
}
```
- Runtime: 4 ms (Beats: 46.06%)
- Memory: 42.40 MB (Beats: 11.08%)

<br>
