# [LeetCode Records](../../README.md) - Question 841 Keys and Rooms

### Attempt 1: Use a LinkedList to store all the keys
```java
class Solution {
    public boolean canVisitAllRooms(List<List<Integer>> rooms) {
        int n = rooms.size();
        boolean[] openedRooms = new boolean[n];

        List<Integer> keys = new LinkedList<>();
        keys.add(0);

        while (!keys.isEmpty()) {
            int room = keys.removeFirst();
            if (!openedRooms[room]) {
                openedRooms[room] = true;
                keys.addAll(rooms.get(room));
            }
        }

        for (boolean openedRoom : openedRooms) {
            if (!openedRoom) {
                return false;
            }
        }

        return true;
    }
}
```
- Runtime: 1 ms (Beats: 76.77%)
- Memory: 44.35 MB (Beats: 34.53%)

<br>
