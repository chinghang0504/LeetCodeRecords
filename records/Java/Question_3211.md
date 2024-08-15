# [LeetCode Records](../../README.md) - Question 3211 Generate Binary Strings Without Adjacent Zeros

### Attempt 1: Use recursion and check the last character
```java
class Solution {
    public List<String> validStrings(int n) {
        if (n == 1) {
            return List.of("0", "1");
        }

        List<String> list = validStrings(n - 1);
        List<String> ans = new ArrayList<>();
        for (String s : list) {
            char lastCh = s.charAt(n - 2);
            if (lastCh == '1') {
                ans.add(s + '0');
            }
            ans.add(s + '1');
        }

        return ans;
    }
}
```
- Runtime: 4 ms (Beats: 41.58%)
- Memory: 45.50 MB (Beats: 79.61%)

<br>
