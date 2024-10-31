# [LeetCode Records](../../README.md) - Question 633 Sum of Square Numbers

### Attempt 1: Use a HashSet to store the squares
```java
class Solution {
    public boolean judgeSquareSum(int c) {
        Set<Long> set = new HashSet<>();

        long num = 0;
        long square = num * num;
        do {
            set.add(square);

            long targetSquare = c - square;
            if (set.contains(targetSquare)) {
                return true;
            }

            num++;
            square = num * num;
        } while (square <= c);

        return false;
    }
}
```
- Runtime: 62 ms (Beats: 9.71%)
- Memory: 54.84 MB (Beats: 5.03%)

<br>
