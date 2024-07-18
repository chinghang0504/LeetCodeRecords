# [LeetCode Records](../../README.md) - Question 2833 Furthest Point From Origin

### Attempt 1: Record the number of '_'
```java
class Solution {
    public int furthestDistanceFromOrigin(String moves) {
        int sum = 0;
        int count = 0;

        for (char ch : moves.toCharArray()) {
            switch (ch) {
                case 'L':
                    sum++;
                    break;
                case 'R':
                    sum--;
                    break;
                case '_':
                    count++;
            }
        }

        return Math.abs(sum) + count;
    }
}
```
- Runtime: 1 ms (Beats: 100.00%)
- Memory: 42.54 MB (Beats: 14.02%)

<br>
