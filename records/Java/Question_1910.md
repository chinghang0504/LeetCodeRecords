# [LeetCode Records](../../README.md) - Question 1910 Remove All Occurrences of a Substring

### Attempt 1: Use replaceFirst() to remove the substring
```java
class Solution {
    public String removeOccurrences(String s, String part) {
        String prevStr = s;
        String nextStr = prevStr.replaceFirst(part, "");

        while (!prevStr.equals(nextStr)) {
            prevStr = nextStr;
            nextStr = prevStr.replaceFirst(part, "");
        }
        
        return prevStr;
    }
}
```
- Runtime: 9 ms (Beats: 18.10%)
- Memory: 44.45 MB (Beats: 29.14%)

<br>
