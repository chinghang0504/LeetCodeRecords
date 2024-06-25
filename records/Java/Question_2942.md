# [LeetCode Records](../../README.md) - Question 2942 Find Words Containing Character

### Attempt 1: Use a nested loop
```java
class Solution {
    public List<Integer> findWordsContaining(String[] words, char x) {
        List<Integer> result = new ArrayList<>();

        int currIndex = 0;
        for (String word : words) {
            for (char ch : word.toCharArray()) {
                if (ch == x) {
                    result.add(currIndex);
                    break;
                }
            }

            currIndex++;
        }

        return result;
    }
}
```
- Runtime: 2 ms (Beats: 57.97%)
- Memory: 44.89 MB (Beats: 31.20%)

<br>
