# [LeetCode Records](../README.md) - Question 46 Permutations

### Attempt 1: Use three loops
```java
class Solution {
    public List<List<Integer>> permute(int[] nums) {
        List<List<Integer>> result = new ArrayList<>();

        // First element
        List<Integer> firstList = new LinkedList<>();
        firstList.add(nums[0]);
        result.add(firstList);

        // Loop for each element
        for (int i = 1; i < nums.length; i++) {
            List<List<Integer>> tempResult = new ArrayList<>();

            // Loop for each list
            Iterator<List<Integer>> iterator = result.iterator();
            while (iterator.hasNext()) {
                List<Integer> targetList = iterator.next();
                int size = targetList.size();

                // Loop for adding an element
                for (int j = 0; j < size + 1; j++) {
                    List<Integer> copyList = new LinkedList<>(targetList);
                    copyList.add(j, nums[i]);
                    tempResult.add(copyList);
                }
            }

            // Update the result
            result = tempResult;
        }

        return result;
    }
}
```
- Runtime: 2 ms (Beats: 49.67%)
- Memory: 44.48 MB (Beats: 42.17%)

<br>
