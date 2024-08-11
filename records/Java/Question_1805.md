# [LeetCode Records](../../README.md) - Question 1805 Number of Different Integers in a String

### Attempt 1: Use a HashSet to save the number strings and a helper function to remove leading zeros
```java
class Solution {
    public int numDifferentIntegers(String word) {
        Set<String> set = new HashSet<>();
        StringBuilder stringBuilder = new StringBuilder();

        for (char ch : word.toCharArray()) {
            if (Character.isDigit(ch)) {
                stringBuilder.append(ch);
            } else if (stringBuilder.length() > 0) {
                set.add(removeLeadingZeros(stringBuilder.toString()));
                stringBuilder = new StringBuilder();
            }
        }
        if (stringBuilder.length() > 0) {
            set.add(removeLeadingZeros(stringBuilder.toString()));
        }

        return set.size();
    }

    private String removeLeadingZeros(String num) {
        char[] arr = num.toCharArray();

        int i = 0;
        while (i < arr.length && arr[i] == '0') {
            i++;
        }
        
        return i == arr.length ? "0" : num.substring(i, arr.length);
    }
}
```
- Runtime: 2 ms (Beats: 98.52%)
- Memory: 42.02 MB (Beats: 51.78%)

<br>
