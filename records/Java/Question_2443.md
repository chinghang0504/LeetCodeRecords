# [LeetCode Records](../../README.md) - Question 2443 Sum of Number and Its Reverse

### Attempt 1: Test every case
```java
class Solution {
    public boolean sumOfNumberAndReverse(int num) {
        for (int i = 0; i <= num / 2; i++) {
            if (isReversed(num - i, i)) {
                return true;
            }
        }

        return false;
    }

    private boolean isReversed(int num1, int num2) {
        char[] arr1 = String.valueOf(num1).toCharArray();
        char[] arr2 = String.valueOf(num2).toCharArray();

        int leftIndex = 0;
        int rightIndex = arr2.length - 1;
        while (leftIndex < arr1.length && rightIndex >= 0) {
            if (arr1[leftIndex] != arr2[rightIndex]) {
                return false;
            }
            leftIndex++;
            rightIndex--;
        }
        while (leftIndex < arr1.length) {
            if (arr1[leftIndex] != '0') {
                return false;
            }
            leftIndex++;
        }

        return true;
    }
}
```
- Runtime: 235 ms (Beats: 25.30%)
- Memory: 44.38 MB (Beats: 18.95%)

<br>
