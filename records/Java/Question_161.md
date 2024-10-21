# [LeetCode Records](../../README.md) - Question 161 One Edit Distance

### Attempt 1: Compare the lengths of strings first
```java
class Solution {
    public boolean isOneEditDistance(String s, String t) {
        char[] arr1 = s.toCharArray();
        char[] arr2 = t.toCharArray();

        if (arr1.length == arr2.length) {
            if (arr1.length == 0) {
                return false;
            }

            int count = 0;
            for (int i = 0; i < arr1.length; i++) {
                if (arr1[i] != arr2[i]) {
                    count++;

                    if (count >= 2) {
                        return false;
                    }
                }
            }

            return count == 1;
        }

        if (arr2.length > arr1.length) {
            char[] temp = arr1;
            arr1 = arr2;
            arr2 = temp;
        }

        if (arr1.length - arr2.length > 1) {
            return false;
        }

        int leftIndex = 0;
        int rightIndex = 0;
        while (rightIndex < arr2.length && arr1[leftIndex] == arr2[rightIndex]) {
            leftIndex++;
            rightIndex++;
        }

        if (rightIndex == arr2.length) {
            return true;
        }

        leftIndex++;
        while (rightIndex < arr2.length && arr1[leftIndex] == arr2[rightIndex]) {
            leftIndex++;
            rightIndex++;
        }

        return rightIndex == arr2.length;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 41.90 MB (Beats: 53.85%)

<br>
