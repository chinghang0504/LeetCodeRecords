# [LeetCode Records](../../README.md) - Question 2728 Count Houses in a Circular Street

### Attempt 1: Close all the doors first
```java
class Solution {
    public int houseCount(Street street, int k) {
        for (int i = 0; i < k; i++) {
            street.closeDoor();
            street.moveRight();
        }

        for (int i = 0; i < k; i++) {
            if (street.isDoorOpen()) {
                return i;
            }

            street.openDoor();
            street.moveRight();
        }

        return k;
    }
}
```
- Runtime: 2 ms (Beats: 78.95%)
- Memory: 44.29 MB (Beats: 68.42%)

<br>
