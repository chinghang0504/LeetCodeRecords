# [LeetCode Records](../../README.md) - Question 353 Design Snake Game

### Attempt 1: 
```java
class SnakeGame {

    private int width;
    private int height;
    private int[][] food;
    private int currFoodIndex;
    private List<int[]> snake;

    public SnakeGame(int width, int height, int[][] food) {
        this.width = width;
        this.height = height;
        this.food = food;
        this.currFoodIndex = 0;
        this.snake = new LinkedList<>();
        this.snake.add(new int[]{0, 0});
    }

    public int move(String direction) {
        int[] newHead = snake.getFirst().clone();

        switch (direction) {
            case "U":
                newHead[0]--;
                break;
            case "D":
                newHead[0]++;
                break;
            case "L":
                newHead[1]--;
                break;
            case "R":
                newHead[1]++;
                break;
        }

        return moveNextPosition(newHead) ? this.snake.size() - 1 : -1;
    }

    private boolean moveNextPosition(int[] newHead) {
        // Hit the wall
        if (newHead[0] < 0 || newHead[0] >= height || newHead[1] < 0 || newHead[1] >= width) {
            return false;
        }

        // Hit the body
        for (int i = 0; i < snake.size() - 1; i++) {
            int[] position = snake.get(i);
            if (position[0] == newHead[0] && position[1] == newHead[1])  {
                return false;
            }
        }

        // Hit the food
        if (this.currFoodIndex < this.food.length) {
            int[] currFood = this.food[this.currFoodIndex];
            if (currFood[0] == newHead[0] && currFood[1] == newHead[1]) {
                this.currFoodIndex++;
                this.snake.addFirst(newHead);
                return true;
            }
        }

        // Hit nothing
        this.snake.removeLast();
        this.snake.addFirst(newHead);
        return true;                                
    }
}
```
- Runtime: 53 ms (Beats: 48.79%)
- Memory: 48.74 MB (Beats: 96.37%)

<br>
