# [LeetCode Records](../../README.md) - Question 2566 Maximum Difference by Remapping a Digit

### Attempt 1: To get the maximum value, find the leftmost digit that is not equal to 9
```java
class Solution {
    public int minMaxDifference(int num) {
        int numCopy = num;
        int[] arr = new int[9];
        int size = 0;
        while (numCopy > 0) {
            arr[size] = numCopy % 10;
            numCopy /= 10;
            size++;
        }

        int max = getMaxValue(arr, size, num);
        int min = getMinValue(arr, size);

        return max - min;
    }

    private int getMaxValue(int[] arr, int size, int num) {
        int targetDigit = -1;

        for (int i = size - 1; i >= 0; i--) {
            if (arr[i] != 9) {
                targetDigit = arr[i];
                break;
            }
        }

        if (targetDigit == -1) {
            return num;
        }

        int value = 0;
        for (int i = size - 1; i >= 0; i--) {
            value *= 10;
            value += arr[i] == targetDigit ? 9 : arr[i];
        }

        return value;
    }

    private int getMinValue(int[] arr, int size) {
        int targetDigit = arr[size - 1];

        int value = 0;
        for (int i = size - 1; i >= 0; i--) {
            value *= 10;
            value += arr[i] == targetDigit ? 0 : arr[i];
        }

        return value;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 40.64 MB (Beats: 29.75%)

<br>
