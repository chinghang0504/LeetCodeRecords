# [LeetCode Records](../../README.md) - Question 1588 Sum of All Odd Length Subarrays

### Attempt 1: Use three loops
```java
class Solution {
    public int sumOddLengthSubarrays(int[] arr) {
        int sum = 0;
        int currLength = 1;

        while (currLength <= arr.length) {
            for (int i = 0; i < arr.length + 1 - currLength; i++) {
                for (int j = 0; j < currLength; j++) {
                    sum += arr[i + j];
                }
            }

            currLength += 2;
        }

        return sum;
    }
}
```
- Runtime: 2 ms (Beats: 60.85%)
- Memory: 41.19 MB (Beats: 54.08%)

<br>
