# [LeetCode Records](../../README.md) - Question 1408 String Matching in an Array

### Attempt 1: Use a nested loop
```java
class Solution {
    public List<String> stringMatching(String[] words) {
        List<String> answer = new ArrayList<>();

        for (int i = 0; i < words.length; i++) {
            for (int j = 0; j < words.length; j++) {
                if (i == j) {
                    continue;
                } else if (words[j].indexOf(words[i]) != -1) {
                    answer.add(words[i]);
                    break;
                }
            }
        }

        return answer;
    }
}
```
- Runtime: 4 ms (Beats: 83.75%)
- Memory: 42.36 MB (Beats: 18.07%)

<br>
