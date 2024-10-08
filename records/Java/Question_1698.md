# [LeetCode Records](../../README.md) - Question 1698 Number of Distinct Substrings in a String

### Attempt 1: Use a HashSet to store the substrings
```java
class Solution {
    public int countDistinct(String s) {
        int size = s.length();
        Set<String> set = new HashSet<>();

        for (int i = size; i >= 1; i--) {
            for (int j = 0; j < size - i + 1; j++) {
                set.add(s.substring(j, j + i));
            }
        }

        return set.size();
    }
}
```
- Runtime: 607 ms (Beats: 33.62%)
- Memory: 114.59 MB (Beats: 33.19%)

<br>
