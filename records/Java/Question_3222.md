# [LeetCode Records](../../README.md) - Question 3222 Find the Winning Player in Coin Game

### Attempt 1: 
```java
class Solution {
    public String losingPlayer(int x, int y) {
        boolean isAliceTurn = true;

        while (x - 1 >= 0 && y - 4 >= 0) {
            x -= 1;
            y -= 4;
            isAliceTurn = !isAliceTurn;
        }

        return isAliceTurn ? "Bob" : "Alice";
    }
}
```
- Runtime: 1 ms (Beats: 22.93%)
- Memory: 41.56 MB (Beats: 63.91%)

<br>

### Attempt 2: Use Math.min()
```java
class Solution {
    public String losingPlayer(int x, int y) {
        int steps = Math.min(x, y / 4);

        return steps % 2 == 0 ? "Bob" : "Alice";
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 41.32 MB (Beats: 87.17%)

<br>
