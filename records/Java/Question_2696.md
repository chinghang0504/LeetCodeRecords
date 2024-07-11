# [LeetCode Records](../../README.md) - Question 2696 Minimum String Length After Removing Substrings

### Attempt 1: Use a LinkedList
```java
class Solution {
    public int minLength(String s) {
        List<Character> list = new LinkedList<>();

        for (char ch : s.toCharArray()) {
            if (list.size() > 0) {
                char lastCh = list.getLast();

                if (ch == 'B' && lastCh == 'A') {
                    list.removeLast();
                    continue;
                } else if (ch == 'D' && lastCh == 'C') {
                    list.removeLast();
                    continue;
                }
            }

            list.addLast(ch);
        }

        return list.size();
    }
}
```
- Runtime: 3 ms (Beats: 88.87%)
- Memory: 44.95 MB (Beats: 12.79%)

<br>
