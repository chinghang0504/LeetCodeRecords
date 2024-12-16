# [LeetCode Records](../../README.md) - Question 2904 Shortest and Lexicographically Smallest Beautiful String

### Attempt 1: Use an ArrayList to record the '1' character indices
```java
class Solution {
    public String shortestBeautifulSubstring(String s, int k) {
        char[] arr = s.toCharArray();
        List<Integer> oneIndices = new ArrayList<>();
        for (int i = 0; i < arr.length; i++) {
            if (arr[i] == '1') {
                oneIndices.add(i);
            }
        }

        int size = oneIndices.size();
        if (size < k) {
            return "";
        }

        int minLen = Integer.MAX_VALUE;
        SortedSet<String> shortestStrings = new TreeSet<>();
        for (int i = 0; i < size - k + 1; i++) {
            int fistIndex = oneIndices.get(i);
            int lastIndex = oneIndices.get(i + k - 1);
            int len = lastIndex - fistIndex + 1;
            if (len < minLen) {
                minLen = len;
                shortestStrings.clear();
                shortestStrings.add(s.substring(fistIndex, lastIndex + 1));
            } else if (len == minLen) {
                shortestStrings.add(s.substring(fistIndex, lastIndex + 1));
            }
        }

        return shortestStrings.first();
    }
}
```
- Runtime: 2 ms (Beats: 69.67%)
- Memory: 42.59 MB (Beats: 78.86%)

<br>
