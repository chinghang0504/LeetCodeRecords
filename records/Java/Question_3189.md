# [LeetCode Records](../../README.md) - Question 3189 Minimum Moves to Get a Peaceful Board

### Attempt 1: Use two int[][] to store the horizontal position and the vertical position counts
```java
class Solution {
    public int minMoves(int[][] rooks) {
        int n = rooks.length;
        int[] horizontalPositionCounts = new int[n];
        int[] verticalPositionCounts = new int[n];

        for (int[] rook : rooks) {
            horizontalPositionCounts[rook[0]]++;
            verticalPositionCounts[rook[1]]++;
        }

        int numOfMoves = 0;
        int[] zeroPositions = new int[n];
        int[] moreThanOnePositions = new int[n];
        int size1 = 0;
        int size2 = 0;
        for (int i = 0; i < n; i++) {
            if (horizontalPositionCounts[i] == 0) {
                zeroPositions[size1] = i;
                size1++;
            } else if (horizontalPositionCounts[i] > 1) {
                for (int j = 0; j < horizontalPositionCounts[i] - 1; j++) {
                    moreThanOnePositions[size2] = i;
                    size2++;
                }
            }
        }
        for (int i = 0; i < size1; i++) {
            numOfMoves += Math.abs(zeroPositions[i] - moreThanOnePositions[i]);
        }

        size1 = 0;
        size2 = 0;
        for (int i = 0; i < n; i++) {
            if (verticalPositionCounts[i] == 0) {
                zeroPositions[size1] = i;
                size1++;
            } else if (verticalPositionCounts[i] > 1) {
                for (int j = 0; j < verticalPositionCounts[i] - 1; j++) {
                    moreThanOnePositions[size2] = i;
                    size2++;
                }
            }
        }
        for (int i = 0; i < size1; i++) {
            numOfMoves += Math.abs(zeroPositions[i] - moreThanOnePositions[i]);
        }

        return numOfMoves;
    }
}
```
- Runtime: 2 ms (Beats: 74.77%)
- Memory: 45.25 MB (Beats: 23.23%)

<br>
