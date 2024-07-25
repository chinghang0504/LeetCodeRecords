# [LeetCode Records](../../README.md) - Question 942 DI String Match

### Attempt 1: Find the pattern and use a loop
```java
class Solution {
    public int[] diStringMatch(String s) {
        int size = s.length();
        int[] answer = new int[size + 1];

        if (s.charAt(0) == 'I') {
            answer[0] = 0;
            answer[1] = 1;
        } else {
            answer[0] = 1;
            answer[1] = 0;
        }

        for (int i = 1; i < size; i++) {
            char ch = s.charAt(i);
            if (ch == 'I') {
                answer[i + 1] = i + 1;
            } else {
                for (int j = 0; j <= i; j++) {
                    answer[j]++;
                }
                answer[i + 1] = 0;
            }
        }
        
        return answer;
    }
}
```
- Runtime: 75 ms (Beats: 11.32%)
- Memory: 45.10 MB (Beats: 38.19%)

<br>
