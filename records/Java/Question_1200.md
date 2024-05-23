# [LeetCode Records](../../README.md) - Question 1200 Minimum Absolute Difference

### Attempt 1: Calculate the minimum absolute difference first
```java
class Solution {
    public List<List<Integer>> minimumAbsDifference(int[] arr) {
        List<List<Integer>> result = new ArrayList<>();

        Arrays.sort(arr);

        int minAbsDiff = Integer.MAX_VALUE;
        for (int i = 0; i < arr.length - 1; i++) {
            minAbsDiff = Math.min(minAbsDiff, arr[i + 1] - arr[i]);
        }

        for (int i = 0; i < arr.length - 1; i++) {
            if (arr[i + 1] - arr[i] == minAbsDiff) {
                result.add(List.of(arr[i], arr[i + 1]));
            }
        }

        return result;
    }
}
```
- Runtime: 18 ms (Beats: 68.41%)
- Memory: 57.06 MB (Beats: 26.55%)

<br>
