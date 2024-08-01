# [LeetCode Records](../../README.md) - Question 2855 Minimum Right Shifts to Sort the Array

### Attempt 1: Use a helper function that check if the array is sorted
```java
class Solution {
    public int minimumRightShifts(List<Integer> nums) {
        int[] arr = new int[nums.size()];
        int size = 0;

        for (int num : nums) {
            arr[size] = num;
            size++;
        }

        int min = arr[0];
        int minIndex = 0;
        for (int i = 1; i < arr.length; i++) {
            if (arr[i] < min) {
                min = arr[i];
                minIndex = i;
            }
        }

        if (minIndex == 0) {
            return isSorted(arr, 0, arr.length) ? 0 : -1;
        }

        return isSorted(arr, 0, minIndex) && isSorted(arr, minIndex, arr.length) && arr[0] >= arr[arr.length - 1] ? arr.length - minIndex : -1;
    }

    private boolean isSorted(int[] arr, int start, int end) {
        for (int i = start; i < end - 1; i++) {
            if (arr[i] > arr[i + 1]) {
                return false;
            }
        }

        return true;
    }
}
```
- Runtime: 1 ms (Beats: 100.00%)
- Memory: 42.40 MB (Beats: 81.22%)

<br>
