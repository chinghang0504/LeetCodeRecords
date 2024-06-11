# [LeetCode Records](../../README.md) - Question 1967 Number of Strings That Appear as Substrings in Word

### Attempt 1: Use contains()
```java
class Solution {
    public int numOfStrings(String[] patterns, String word) {
        int count = 0;

        for (String str : patterns) {
            if (word.contains(str)) {
                count++;
            }
        }
        
        return count;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 42.13 MB (Beats: 18.84%)

<br>
