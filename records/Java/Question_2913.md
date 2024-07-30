# [LeetCode Records](../../README.md) - Question 2913 Subarrays Distinct Element Sum of Squares I

### Attempt 1: Use two helper functions to calculate the sum of the squares of distinct counts of all the subarrays
```java
class Solution {
    public int sumCounts(List<Integer> nums) {
        int[] arr = new int[nums.size()];
        int size = 0;

        for (int num : nums) {
            arr[size] = num;
            size++;
        }

        int sum = 0;
        for (int i = 1; i <= size; i++) {
            sum += getSquareOfDistinctCounts(arr, i);
        }

        return sum;
    }

    private int getSquareOfDistinctCounts(int[] arr, int n) {
        int sum = 0;

        for (int i = 0; i < arr.length - n + 1; i++) {
            int distinctCount = getDistinctCount(arr, i, i + n);
            sum += distinctCount * distinctCount;
        }

        return sum;
    }

    private int getDistinctCount(int[] arr, int startIndex, int endIndex) {
        boolean[] saved = new boolean[101];
        int count = 0;

        for (int i = startIndex; i < endIndex; i++) {
            if (!saved[arr[i]]) {
                count++;
                saved[arr[i]] = true;
            }
        }

        return count;
    }
}
```
- Runtime: 14 ms (Beats: 44.92%)
- Memory: 44.77 MB (Beats: 52.50%)

<br>
