# [LeetCode Records](../../README.md) - Question 2390 Removing Stars From a String

### Attempt 1: Use an ArrayList to store the characters
```java
class Solution {
    public String removeStars(String s) {
        List<Character> list = new ArrayList<>();

        for (char ch : s.toCharArray()) {
            if (ch == '*') {
                if (!list.isEmpty()) {
                    list.removeLast();
                }
            } else {
                list.addLast(ch);
            }
        }

        StringBuilder stringBuilder = new StringBuilder();
        for (char ch : list) {
            stringBuilder.append(ch);
        }

        return stringBuilder.toString();
    }
}
```
- Runtime: 28 ms (Beats: 90.94%)
- Memory: 45.32 MB (Beats: 91.17%)

<br>
