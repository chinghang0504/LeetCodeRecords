# [LeetCode Records](../../README.md) - Question 1461 Check If a String Contains All Binary Codes of Size K

### Attempt 1: Use a HashSet to store all the substrings with the k length
```java
class Solution {
    public boolean hasAllCodes(String s, int k) {
        Set<String> set = new HashSet<>();

        int len = s.length();
        for (int i = 0; i < len - k + 1; i++) {
            set.add(s.substring(i, i + k));
        }
        
        return set.size() == (int)Math.pow(2, k);
    }
}
```
- Runtime: 164 ms (Beats: 53.74%)
- Memory: 67.84 MB (Beats: 77.28%)

<br>
