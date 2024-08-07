# [LeetCode Records](../../README.md) - Question 2900 Longest Unequal Adjacent Groups Subsequence I

### Attempt 1: Count zero first and one first
```java
class Solution {
    public List<String> getLongestSubsequence(String[] words, int[] groups) {
        int zeroFirstCount = 0;
        boolean isZero = true;
        for (int group : groups) {
            if (isZero) {
                if (group == 0) {
                    isZero = !isZero;
                    zeroFirstCount++;
                }
            } else {
                if (group == 1) {
                    isZero = !isZero;
                    zeroFirstCount++;
                }
            }
        }

        int oneFirstCount = 0;
        isZero = false;
        for (int group : groups) {
            if (isZero) {
                if (group == 0) {
                    isZero = !isZero;
                    oneFirstCount++;
                }
            } else {
                if (group == 1) {
                    isZero = !isZero;
                    oneFirstCount++;
                }
            }
        }

        List<String> answer = new ArrayList<>();
        isZero = zeroFirstCount >= oneFirstCount;
        for (int i = 0; i < groups.length; i++) {
            if (isZero) {
                if (groups[i] == 0) {
                    isZero = !isZero;
                    answer.add(words[i]);
                }
            } else {
                if (groups[i] == 1) {
                    isZero = !isZero;
                    answer.add(words[i]);
                }
            }
        }

        return answer;
    }
}
```
- Runtime: 1 ms (Beats: 95.75%)
- Memory: 44.54 MB (Beats: 89.78%)

<br>
