# [LeetCode Records](../../README.md) - Question 2515 Shortest Distance to Target String in a Circular Array

### Attempt 1: Compare the left and the right distances
```java
class Solution {
    public int closetTarget(String[] words, String target, int startIndex) {
        int leftDistance = -1;
        int rightDistance = -1;

        for (int i = startIndex; i < words.length; i++) {
            if (words[i].equals(target)) {
                rightDistance = i - startIndex;
                break;
            }
        }
        if (rightDistance == -1) {
            for (int i = 0; i < startIndex; i++) {
                if (words[i].equals(target)) {
                    rightDistance = i + words.length - startIndex;
                    break;
                }
            }
        }

        for (int i = startIndex - 1; i >= 0; i--) {
            if (words[i].equals(target)) {
                leftDistance = startIndex - i;
                break;
            }
        }
        if (leftDistance == -1) {
            for (int i = words.length - 1; i > startIndex; i--) {
                if (words[i].equals(target)) {
                    leftDistance = startIndex + words.length - i;
                    break;
                }
            }
        }

        if (leftDistance != -1 && rightDistance != -1) {
            return Math.min(leftDistance, rightDistance);
        } else if (leftDistance != -1) {
            return leftDistance;
        } else if (rightDistance != -1) {
            return rightDistance;
        } else {
            return -1;
        }
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 44.54 MB (Beats: 51.13%)

<br>
