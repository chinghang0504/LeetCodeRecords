# [LeetCode Records](../../README.md) - Question 1710 Maximum Units on a Truck

### Attempt 1: Use Arrays.sort() to sort box types first
```java
class Solution {
    public int maximumUnits(int[][] boxTypes, int truckSize) {
        Arrays.sort(boxTypes, new Comparator<int[]>() {
            @Override
            public int compare(int[] o1, int[] o2) {
                return o2[1] - o1[1];
            }
        });

        int totalUnit = 0;
        int totalSize = 0;
        for (int[] boxType : boxTypes) {
            int minSize = Math.min(boxType[0], truckSize - totalSize);
            totalSize += minSize;
            totalUnit += boxType[1] * minSize;

            if (totalSize == truckSize) {
                break;
            }
        }

        return totalUnit;
    }
}
```
- Runtime: 9 ms (Beats: 92.14%)
- Memory: 44.85 MB (Beats: 67.61%)

<br>
