# [LeetCode Records](../../README.md) - Question 1564 Put Boxes Into the Warehouse I

### Attempt 1: Update the warehouse heights first
```java
class Solution {
    public int maxBoxesInWarehouse(int[] boxes, int[] warehouse) {
        int currMaxHeight = warehouse[0];
        for (int i = 1; i < warehouse.length; i++) {
            if (warehouse[i] > currMaxHeight) {
                warehouse[i] = currMaxHeight;
            } else if (warehouse[i] < currMaxHeight) {
                currMaxHeight = warehouse[i];
            }
        }

        Arrays.sort(boxes);

        int count = 0;
        int leftIndex = 0;
        int rightIndex = warehouse.length - 1;

        while (leftIndex < boxes.length && rightIndex >= 0) {
            if (warehouse[rightIndex] >= boxes[leftIndex]) {
                count++;
                rightIndex--;
                leftIndex++;
            } else {
                rightIndex--;
            }
        }

        return count;
    }
}
```
- Runtime: 17 ms (Beats: 90.00%)
- Memory: 61.19 MB (Beats: 82.50%)

<br>
