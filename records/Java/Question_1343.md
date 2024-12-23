# [LeetCode Records](../../README.md) - Question 1343 Number of Sub-arrays of Size K and Average Greater than or Equal to Threshold

### Attempt 1: Track the current sum
```java
class Solution {
    public int numOfSubarrays(int[] arr, int k, int threshold) {
        int target = threshold * k;
        int count = 0;
        int currSum = 0;
        for (int i = 0; i < k; i++) {
            currSum += arr[i];
        }
        if (currSum >= target) {
            count++;
        }

        for (int i = k; i < arr.length; i++) {
            currSum = currSum + arr[i] - arr[i - k];
            if (currSum >= target) {
                count++;
            }
        }

        return count;
    }
}
```
- Runtime: 2 ms (Beats: 100.00%)
- Memory: 60.95 MB (Beats: 42.43%)

<br>
