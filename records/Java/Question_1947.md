# [LeetCode Records](../../README.md) - Question 1947 Maximum Compatibility Score Sum

### Attempt 1: Use backtracking to test every possible solution
```java
class Solution {

    private int m;
    private int n;
    private int[][] scores;
    private int maxTotalScore;
    private boolean[] selectedMentors;

    public int maxCompatibilitySum(int[][] students, int[][] mentors) {
        m = students.length;
        n = students[0].length;
        scores = new int[m][m];

        for (int i = 0; i < m; i++) {
            for (int j = 0; j < m; j++) {
                scores[i][j] = getScore(students[i], mentors[j]);
            }
        }

        maxTotalScore = 0;
        selectedMentors = new boolean[m];
        compareAllScores(0, 0);

        return maxTotalScore;
    }

    private int getScore(int[] student, int[] mentor) {
        int sum = 0;
        for (int i = 0; i < student.length; i++) {
            sum += student[i] == mentor[i] ? 1 : 0;
        }
        return sum;
    }

    private void compareAllScores(int currStudent, int currTotalScore) {
        if (currStudent == m) {
            maxTotalScore = Math.max(maxTotalScore, currTotalScore);
            return;
        }

        for (int j = 0; j < m; j++) {
            if (!selectedMentors[j]) {
                selectedMentors[j] = true;
                compareAllScores(currStudent + 1, currTotalScore + scores[currStudent][j]);
                selectedMentors[j] = false;
            }
        }
    }
}
```
- Runtime: 17 ms (Beats: 76.49%)
- Memory: 41.51 MB (Beats: 40.40%)

<br>
