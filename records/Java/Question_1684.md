# [LeetCode Records](../../README.md) - Question 1684 Count the Number of Consistent Strings

### Attempt 1: Use a HashSet
```java
class Solution {
    public int countConsistentStrings(String allowed, String[] words) {
        Set<Character> set = new HashSet<>();

        for (char ch : allowed.toCharArray()) {
            set.add(ch);
        }

        int count = 0;
        for (String word : words) {
            boolean isMatch = true;
            for (char ch : word.toCharArray()) {
                if (!set.contains(ch)) {
                    isMatch = false;
                    break;
                }
            }
            if (isMatch) {
                count++;
            }
        }

        return count;
    }
}
```
- Runtime: 12 ms (Beats: 68.55%)
- Memory: 45.39 MB (Beats: 46.68%)

<br>
