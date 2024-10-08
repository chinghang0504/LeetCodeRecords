# [LeetCode Records](../../README.md) - Question 1580 Put Boxes Into the Warehouse II

### Attempt 1: Use an int[] to update the maximum height of each room in warehouse
```java
class Solution {
    public int maxBoxesInWarehouse(int[] boxes, int[] warehouse) {
        int[] updatedWarehouse = new int[warehouse.length];

        int leftMax = warehouse[0];
        for (int i = 0; i < warehouse.length; i++) {
            if (warehouse[i] < leftMax) {
                leftMax = warehouse[i];
            }
            updatedWarehouse[i] = leftMax;
        }

        int rightMax = warehouse[warehouse.length - 1];
        for (int i = warehouse.length - 1; i >= 0; i--) {
            if (warehouse[i] < rightMax) {
                rightMax = warehouse[i];
            }

            updatedWarehouse[i] = Math.max(updatedWarehouse[i], rightMax);
        }

        Arrays.sort(updatedWarehouse);
        Arrays.sort(boxes);

        int count = 0;
        int boxIndex = boxes.length - 1;
        int warehouseIndex = warehouse.length - 1;

        while (boxIndex >= 0 && warehouseIndex >= 0) {
            if (boxes[boxIndex] <= updatedWarehouse[warehouseIndex]) {
                count++;
                warehouseIndex--;
            }

            boxIndex--;
        }

        return count;
    }
}
```
- Runtime: 24 ms (Beats: 50.00%)
- Memory: 61.26 MB (Beats: 53.85%)

<br>
