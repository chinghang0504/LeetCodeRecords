# [LeetCode Records](../../README.md) - Question 3083 Existence of a Substring in a String and Its Reverse

### Attempt 1: Use StringBuilder.reverse()
```java
class Solution {
    public boolean isSubstringPresent(String s) {
        StringBuilder stringBuilder = new StringBuilder(s);
        String target = stringBuilder.reverse().toString();

        int size = target.length();
        for (int i = 0; i < size - 1; i++) {
            if (target.indexOf(s.substring(i, i + 2)) != -1) {
                return true;
            }
        }

        return false;
    }
}
```
- Runtime: 1 ms (Beats: 100.00%)
- Memory: 42.27 MB (Beats: 65.12%)

<br>
