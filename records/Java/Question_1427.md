# [LeetCode Records](../../README.md) - Question 1427 Perform String Shifts

### Attempt 1: Record the head index
```java
class Solution {
    public String stringShift(String s, int[][] shift) {
        int headIndex = 0;
        char[] arr = s.toCharArray();
        int size = arr.length;

        for (int[] operation : shift) {
            if (operation[0] == 0) {
                headIndex += operation[1] % size;
            } else {
                headIndex -= operation[1] % size;
            }

            if (headIndex < 0) {
                headIndex += size;
            } else if (headIndex >= size) {
                headIndex -= size;
            }
        }

        StringBuilder stringBuilder = new StringBuilder();
        for (int i = headIndex; i < size; i++) {
            stringBuilder.append(arr[i]);
        }
        for (int i = 0; i < headIndex; i++) {
            stringBuilder.append(arr[i]);
        }

        return stringBuilder.toString();
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 41.44 MB (Beats: 75.98%)

<br>
