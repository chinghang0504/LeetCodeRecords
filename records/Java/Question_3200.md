# [LeetCode Records](../../README.md) - Question 3200 Maximum Height of a Triangle

### Attempt 1: Count from red and blue
```java
class Solution {
    public int maxHeightOfTriangle(int red, int blue) {
        int redCopy = red;
        int blueCopy = blue;
        int redFirst = 0;
        int blueFirst = 0;

        int i = 1;
        while (true) {
            if (redCopy - i >= 0) {
                redCopy -= i;
                redFirst++;
            } else {
                break;
            }
            i++;

            if (blueCopy - i >= 0) {
                blueCopy -= i;
                redFirst++;
            } else {
                break;
            }
            i++;
        }

        i = 1;
        redCopy = red;
        blueCopy = blue;
        while (true) {
            if (blueCopy - i >= 0) {
                blueCopy -= i;
                blueFirst++;
            } else {
                break;
            }
            i++;

            if (redCopy - i >= 0) {
                redCopy -= i;
                blueFirst++;
            } else {
                break;
            }
            i++;
        }

        return Math.max(redFirst, blueFirst);
    }
}
```
- Runtime: 1 ms (Beats: 85.10%)
- Memory: 40.64 MB (Beats: 66.83%)

<br>
