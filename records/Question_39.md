# [LeetCode Records](../README.md) - Question 39 Combination Sum

### Attempt 1: Create a new ArrayList for each possible case
```java
class Solution {
    public List<List<Integer>> combinationSum(int[] candidates, int target) {
        List<List<Integer>> result = new ArrayList<>();

        for (int i = 0; i < candidates.length; i++) {
            List<Integer> data = new ArrayList<>();
            data.add(candidates[i]);
            combinationSumRecursion(candidates, target, result, i, candidates[i], data);
        }

        return result;
    }

    public void combinationSumRecursion(int[] candidates, int target, List<List<Integer>> result, int currIndex, int currValue, List<Integer> data) {
        if (currValue > target) {
            return;
        } else if (currValue == target) {
            result.add(data);
            return;
        }

        for (int i = currIndex; i < candidates.length; i++) {
            List<Integer> newData = new ArrayList<>(data);
            newData.add(candidates[i]);
            combinationSumRecursion(candidates, target, result, i, currValue + candidates[i], newData);
        }
    }
}
```
- Runtime: 5 ms (Beats: 12.25%)
- Memory: 45.04 MB (Beats: 9.23%)

<br>
