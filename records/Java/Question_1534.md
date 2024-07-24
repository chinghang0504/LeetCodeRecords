# [LeetCode Records](../../README.md) - Question 1534 Count Good Triplets

### Attempt 1: Use a nested loop
```java
class Solution {
    public int countGoodTriplets(int[] arr, int a, int b, int c) {
        int count = 0;

        for (int i = 0; i < arr.length - 2; i++) {
            for (int j = i + 1; j < arr.length - 1; j++) {
                if (Math.abs(arr[i] - arr[j]) > a) {
                    continue;
                }

                for (int k = j + 1; k < arr.length; k++) {
                    if (Math.abs(arr[j] - arr[k]) <= b && Math.abs(arr[i] - arr[k]) <= c) {
                        count++;
                    }
                }
            }
        }

        return count;
    }
}
```
- Runtime: 10 ms (Beats: 89.59%)
- Memory: 41.64 MB (Beats: 6.19%)

<br>
