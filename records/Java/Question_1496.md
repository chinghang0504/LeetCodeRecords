# [LeetCode Records](../../README.md) - Question 1496 Path Crossing

### Attempt 1: Use a HashSet to record the previous Coordinates
```java
class Solution {
    private static class Coordinates {
        int x;
        int y;

        Coordinates(int x, int y) {
            this.x = x;
            this.y = y;
        }

        @Override
        public boolean equals(Object o) {
            if (this == o) return true;
            if (o == null || getClass() != o.getClass()) return false;
            Coordinates that = (Coordinates) o;
            return x == that.x && y == that.y;
        }

        @Override
        public int hashCode() {
            return Objects.hash(x, y);
        }
    }

    public boolean isPathCrossing(String path) {
        Set<Coordinates> set = new HashSet<>();

        Coordinates curr = new Coordinates(0, 0);
        set.add(curr);

        for (char ch : path.toCharArray()) {
            switch (ch) {
                case 'N':
                    curr = new Coordinates(curr.x, curr.y + 1);
                    break;
                case 'S':
                    curr = new Coordinates(curr.x, curr.y - 1);
                    break;
                case 'E':
                    curr = new Coordinates(curr.x - 1, curr.y);
                    break;
                case 'W':
                    curr = new Coordinates(curr.x + 1, curr.y);
                    break;
            }

            if (set.contains(curr)) {
                return true;
            } else {
                set.add(curr);
            }
        }

        return false;
    }
}
```
- Runtime: 1 ms (Beats: 98.98%)
- Memory: 42.09 MB (Beats: 42.88%)

<br>
