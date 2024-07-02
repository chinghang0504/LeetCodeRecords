# [LeetCode Records](../../README.md) - Question 1816 Truncate Sentence

### Attempt 1: 
```java
class Solution {
    public String truncateSentence(String s, int k) {
        StringBuilder stringBuilder = new StringBuilder();
        int count = 0;

        for (char ch : s.toCharArray()) {
            if (ch == ' ') {
                count++;
                if (count == k) {
                    break;
                }
            }

            stringBuilder.append(ch);
        }

        return stringBuilder.toString();
    }
}
```
- Runtime: 1 ms (Beats: 74.72%)
- Memory: 41.66 MB (Beats: 60.86%)

<br>
