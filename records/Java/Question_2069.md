# [LeetCode Records](../../README.md) - Question 2069 Walking Robot Simulation II

### Attempt 1: Use perimeter to reduce the steps
```java
class Robot {

    private int width;
    private int height;
    private int perimeter;
    private int currX;
    private int currY;
    private int direction;

    public Robot(int width, int height) {
        this.width = width;
        this.height = height;
        this.perimeter = width + width + height + height - 4;
        this.currX = 0;
        this.currY = 0;
        this.direction = 0;
    }
    
    public void step(int num) {
        num %= perimeter;
        if (currX == 0) {
            if (currY == 0) {
                direction = 3;
            } else if (currY == height - 1) {
                direction = 2;
            }
        } else if (currX == width - 1) {
            if (currY == 0) {
                direction = 0;
            } else if (currY == height - 1) {
                direction = 1;
            }
        }

        for (int i = 0; i < num; i++) {
            if (direction == 0) {
                if (currX + 1 < width) {
                    currX = currX + 1;
                } else {
                    direction = 1;
                    currY = currY + 1;
                }
            } else if (direction == 1) {
                if (currY + 1 < height) {
                    currY = currY + 1;
                } else {
                    direction = 2;
                    currX = currX - 1;
                }
            } else if (direction == 2) {
                if (currX - 1 >= 0) {
                    currX = currX - 1;
                } else {
                    direction = 3;
                    currY = currY - 1;
                }
            } else {
                if (currY - 1 >= 0) {
                    currY = currY - 1;
                } else {
                    direction = 0;
                    currX = currX + 1;
                }
            }
        }
    }
    
    public int[] getPos() {
        return new int[]{ currX, currY };
    }
    
    public String getDir() {
        if (direction == 0) {
            return "East";
        } else if (direction == 1) {
            return "North";
        } else if (direction == 2) {
            return "West";
        } else {
            return "South";
        }
    }
}

/**
 * Your Robot object will be instantiated and called as such:
 * Robot obj = new Robot(width, height);
 * obj.step(num);
 * int[] param_2 = obj.getPos();
 * String param_3 = obj.getDir();
 */
```
- Runtime: 75 ms (Beats: 62.92%)
- Memory: 55.64 MB (Beats: 53.93%)

<br>
