# [LeetCode Records](../../README.md) - Question 1089 Duplicate Zeros

### Attempt 1: Create another array to record the new values
```java
class Solution {
    public void duplicateZeros(int[] arr) {
        int[] result = new int[arr.length + 1];
        int curr = 0;

        for (int num : arr) {
            if (curr >= arr.length) {
                break;
            }

            if (num != 0) {
                result[curr] = num;
                curr++;
            } else {
                result[curr] = 0;
                result[curr + 1] = 0;
                curr += 2;
            }
        }

        for (int i = 0; i < arr.length; i++) {
            arr[i] = result[i];
        }
    }
}
```
- Runtime: 1 ms (Beats: 97.21%)
- Memory: 44.23 MB (Beats: 90.54%)

<br>
