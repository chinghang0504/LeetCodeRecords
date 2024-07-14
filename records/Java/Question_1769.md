# [LeetCode Records](../../README.md) - Question 1769 Minimum Number of Operations to Move All Balls to Each Box

### Attempt 1: Use a nested loop
```java
class Solution {
    public int[] minOperations(String boxes) {
        char[] arr = boxes.toCharArray();
        int[] answer = new int[arr.length];

        for (int i = 0; i < answer.length; i++) {
            for (int j = 0; j < i; j++) {
                if (arr[j] == '1') {
                    answer[i] += i - j;
                }
            }
            for (int j = i + 1; j < answer.length; j++) {
                if (arr[j] == '1') {
                    answer[i] += j - i;
                }
            }
        }

        return answer;
    }
}
```
- Runtime: 56 ms (Beats: 66.64%)
- Memory: 44.92 MB (Beats: 13.67%)

<br>
