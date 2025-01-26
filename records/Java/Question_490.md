# [LeetCode Records](../../README.md) - Question 490 The Maze

### Attempt 1: Use a LinkedList to store the possible positions
```java
class Solution {
    public boolean hasPath(int[][] maze, int[] start, int[] destination) {
        int m = maze.length;
        int n = maze[0].length;
        List<int[]> positionList = new LinkedList<>();
        positionList.add(start);
        maze[start[0]][start[1]] = 2;

        while (!positionList.isEmpty()) {
            int[] position = positionList.removeFirst();
            if (position[0] == destination[0] && position[1] == destination[1]) {
                return true;
            }

            // Up
            int i = position[0];
            int j = position[1];
            while (i - 1 >= 0 && maze[i - 1][j] != 1) {
                i--;
            }
            if (maze[i][j] != 2) {
                maze[i][j] = 2;
                positionList.add(new int[]{ i, j });
            }

            // Down
            i = position[0];
            j = position[1];
            while (i + 1 < m && maze[i + 1][j] != 1) {
                i++;
            }
            if (maze[i][j] != 2) {
                maze[i][j] = 2;
                positionList.add(new int[]{ i, j });
            }

            // Left
            i = position[0];
            j = position[1];
            while (j - 1 >= 0 && maze[i][j - 1] != 1) {
                j--;
            }
            if (maze[i][j] != 2) {
                maze[i][j] = 2;
                positionList.add(new int[]{ i, j });
            }

            // Right
            i = position[0];
            j = position[1];
            while (j + 1 < n && maze[i][j + 1] != 1) {
                j++;
            }
            if (maze[i][j] != 2) {
                maze[i][j] = 2;
                positionList.add(new int[]{ i, j });
            }
        }

        return false;
    }
}
```
- Runtime: 5 ms (Beats: 58.73%)
- Memory: 45.63 MB (Beats: 30.42%)

<br>

### Attempt 2: Use depth first search algorithm to search the next position
```java
class Solution {

    private int m;
    private int n;
    private int[][] maze;
    private int[] destination;

    public boolean hasPath(int[][] maze, int[] start, int[] destination) {
        m = maze.length;
        n = maze[0].length;
        this.maze = maze;
        this.destination = destination;

        return hasPathRecursion(start[0], start[1]);
    }

    private boolean hasPathRecursion(int startI, int startJ) {
        if (startI == destination[0] && startJ == destination[1]) {
            return true;
        } else if (maze[startI][startJ] != 0) {
            return false;
        }
        
        maze[startI][startJ] = 2;

        int i = startI;
        int j = startJ;
        while (i - 1 >= 0 && maze[i - 1][j] != 1) {
            i--;
        }
        if (hasPathRecursion(i, j)) {
            return true;
        }

        i = startI;
        j = startJ;
        while (i + 1 < m && maze[i + 1][j] != 1) {
            i++;
        }
        if (hasPathRecursion(i, j)) {
            return true;
        }

        i = startI;
        j = startJ;
        while (j - 1 >= 0 && maze[i][j - 1] != 1) {
            j--;
        }
        if (hasPathRecursion(i, j)) {
            return true;
        }

        i = startI;
        j = startJ;
        while (j + 1 < n && maze[i][j + 1] != 1) {
            j++;
        }
        if (hasPathRecursion(i, j)) {
            return true;
        }

        return false;
    }
}
```
- Runtime: 1 ms (Beats: 99.88%)
- Memory: 45.30 MB (Beats: 62.72%)

<br>
