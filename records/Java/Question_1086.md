# [LeetCode Records](../../README.md) - Question 1086 High Five

### Attempt 1: Use an int[][] to save scores and a boolean[] to save ids
```java
class Solution {
    public int[][] highFive(int[][] items) {
        int[][] scores = new int[1001][101];
        boolean[] ids = new boolean[1001];

        for (int[] item : items) {
            int id = item[0];
            int score = item[1];
            scores[id][score]++;
            ids[id] = true;
        }

        int[][] answer = new int[1001][2];
        int size = 0;

        for (int i = 1; i < 1001; i++) {
            if (ids[i]) {
                answer[size][0] = i;
                answer[size][1] = getAverage(scores[i]);
                size++;
            }
        }

        return Arrays.copyOf(answer, size);
    }

    private int getAverage(int[] scores) {
        int sum = 0;

        int i = 100;
        int j = 0;
        while (i >= 0 && j < 5) {
            if (scores[i] > 0) {
                sum += i;
                scores[i]--;
                j++;
            } else {
                i--;
            }
        }

        return sum / 5;
    }
}
```
- Runtime: 3 ms (Beats: 99.18%)
- Memory: 45.40 MB (Beats: 6.38%)

<br>
