# [LeetCode Records](../../README.md) - Question 1047 Remove All Adjacent Duplicates In String

### Attempt 1: Use an ArrayList
```java
class Solution {
    public String removeDuplicates(String s) {
        List<Character> list = new ArrayList<>();
        char[] arr = s.toCharArray();

        for (char ch : arr) {
            if (list.size() > 0 && list.getLast() == ch) {
                list.removeLast();
            } else {
                list.addLast(ch);
            }
        }

        StringBuilder stringBuilder = new StringBuilder(list.size());
        for (char ch : list) {
            stringBuilder.append(ch);
        }
        
        return stringBuilder.toString();
    }
}
```
- Runtime: 13 ms (Beats: 77.53%)
- Memory: 45.24 MB (Beats: 57.27%)

<br>
