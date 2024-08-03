# [LeetCode Records](../../README.md) - Question 2660 Determine the Winner of a Bowling Game

### Attempt 1: Use a helper function that calculates the total score
```java
class Solution {
    public int isWinner(int[] player1, int[] player2) {
        int totalScore1 = getTotalScore(player1);
        int totalScore2 = getTotalScore(player2);

        if (totalScore1 > totalScore2) {
            return 1;
        } else if (totalScore1 < totalScore2) {
            return 2;
        } else {
            return 0;
        }
    }

    private int getTotalScore(int[] player) {
        int totalScore = 0;

        if (player.length >= 1) {
            totalScore += player[0];
        }
        if (player.length >= 2) {
            totalScore += player[0] == 10 ? player[1] * 2 : player[1];
        }

        for (int i = 2; i < player.length; i++) {
            totalScore += player[i - 1] == 10 || player[i - 2] == 10 ? player[i] * 2 : player[i];
        }
        
        return totalScore;
    }
}
```
- Runtime: 1 ms (Beats: 100.00%)
- Memory: 45.22 MB (Beats: 14.48%)

<br>
