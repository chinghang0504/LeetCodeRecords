# [LeetCode Records](../../README.md) - Question 1619 Mean of Array After Removing Some Elements

### Attempt 1: Sort the array first
```java
class Solution {
    public double trimMean(int[] arr) {
        Arrays.sort(arr);

        int startIndex = (int)(arr.length * 0.05);
        int endIndex = (int)(arr.length * 0.95);

        double sum = 0.0;
        for (int i = startIndex; i < endIndex; i++) {
            sum += arr[i];
        }

        return sum / (endIndex - startIndex);
    }
}
```
- Runtime: 3 ms (Beats: 97.53%)
- Memory: 43.53 MB (Beats: 92.16%)

<br>
