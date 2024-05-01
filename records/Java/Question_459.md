# [LeetCode Records](../../README.md) - Question 459 Repeated Substring Pattern

### Attempt 1: Loop for checking each substring
```java
class Solution {
    public boolean repeatedSubstringPattern(String s) {
        int size = s.length();

        for (int i = 2; i <= size; i++) {
            if (size % i != 0) {
                continue;
            }

            int subStringSize = size / i;
            int begin = 0;
            int end = subStringSize;
            String subString = s.substring(begin, end);

            boolean allEquals = true;
            for (int j = 0; j < i - 1; j++) {
                begin = end;
                end += subStringSize;
                String nextSubString = s.substring(begin, end);
                if (!subString.equals(nextSubString)) {
                    allEquals = false;
                    break;
                }
            }

            if (allEquals) {
                return true;
            }
        }

        return false;
    }
}
```
- Runtime: 5 ms (Beats: 98.11%)
- Memory: 45.00 MB (Beats: 51.83%)

<br>
