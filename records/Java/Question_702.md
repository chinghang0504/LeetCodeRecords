# [LeetCode Records](../../README.md) - Question 702 Search in a Sorted Array of Unknown Size

### Attempt 1: Find the maximum and the minimum indices first
```java
/**
 * // This is ArrayReader's API interface.
 * // You should not implement it, or speculate about its implementation
 * interface ArrayReader {
 *     public int get(int index) {}
 * }
 */

class Solution {
    public int search(ArrayReader reader, int target) {
        int minIndex = 0;
        int maxIndex = 1;
        while (true) {
            int val = reader.get(maxIndex);
            if (target < val) {
                break;
            } else if (target > val) {
                minIndex = maxIndex;
                maxIndex *= 2;
            } else {
                return maxIndex;
            }
        }

        int middleIndex;
        while (minIndex <= maxIndex) {
            middleIndex = (minIndex + maxIndex) / 2;
            int val = reader.get(middleIndex);
            if (target == val) {
                return middleIndex;
            } else if (target < val) {
                maxIndex = middleIndex - 1;
            } else {
                minIndex = middleIndex + 1;
            }
        }

        return -1;
    }
}
```
- Runtime: 1 ms (Beats: 100.00%)
- Memory: 45.28 MB (Beats: 69.16%)

<br>
