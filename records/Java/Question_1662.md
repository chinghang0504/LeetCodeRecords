# [LeetCode Records](../../README.md) - Question 1662 Check If Two String Arrays are Equivalent

### Attempt 1: Use StringBuilder
```java
class Solution {
    public boolean arrayStringsAreEqual(String[] word1, String[] word2) {
        StringBuilder stringBuilder1 = new StringBuilder();
        StringBuilder stringBuilder2 = new StringBuilder();

        for (String str : word1) {
            stringBuilder1.append(str);
        }
        for (String str : word2) {
            stringBuilder2.append(str);
        }

        return stringBuilder1.toString().equals(stringBuilder2.toString());
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 41.45 MB (Beats: 44.24%)

<br>
