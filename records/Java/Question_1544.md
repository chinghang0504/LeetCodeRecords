# [LeetCode Records](../../README.md) - Question 1544 Make The String Great

### Attempt 1: Use a LinkedList to get the previous characters
```java
class Solution {
    public String makeGood(String s) {
        char[] arr = s.toCharArray();
        List<Character> list = new LinkedList<>();

        for (char ch : arr) {
            if (list.size() == 0) {
                list.add(ch);
                continue;
            }
            
            char lastCh = list.getLast();
            boolean isLastChUpper = Character.isUpperCase(lastCh);
            boolean isChUpper = Character.isUpperCase(ch);
            if (isLastChUpper != isChUpper && Character.toLowerCase(lastCh) == Character.toLowerCase(ch)) {
                list.removeLast();
            } else {
                list.add(ch);
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
- Runtime: 3 ms (Beats: 57.93%)
- Memory: 41.92 MB (Beats: 71.85%)

<br>
