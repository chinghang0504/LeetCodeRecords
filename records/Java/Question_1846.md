# [LeetCode Records](../../README.md) - Question 1846 Maximum Element After Decreasing and Rearranging

### Attempt 1: Use Arrays.sort() to the array
```java
class Solution {
    public int maximumElementAfterDecrementingAndRearranging(int[] arr) {
        Arrays.sort(arr);
        
        arr[0] = 1;

        for (int i = 1; i < arr.length; i++) {
            if (arr[i] - arr[i - 1] > 1) {
                arr[i] = arr[i - 1] + 1;
            }
        }

        return arr[arr.length - 1];
    }
}
```
- Runtime: 5 ms (Beats: 89.35%)
- Memory: 57.68 MB (Beats: 54.63%)

<br>
