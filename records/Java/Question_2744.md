# [LeetCode Records](../../README.md) - Question 2744 Find Maximum Number of String Pairs

### Attempt 1: Use a HashSet to record strings
```java
class Solution {
    public int maximumNumberOfStringPairs(String[] words) {
        Set<String> set = new HashSet<>();
        int count = 0;

        for (String word : words) {
            String reversedStr = getReversedString(word);
            if (set.contains(reversedStr)) {
                count++;
            } else {
                set.add(word);
            }
        }

        return count;
    }

    private String getReversedString(String str) {
        StringBuilder stringBuilder = new StringBuilder(str);
        return stringBuilder.reverse().toString();
    }
}
```
- Runtime: 2 ms (Beats: 79.25%)
- Memory: 43.32 MB (Beats: 44.81%)

<br>
