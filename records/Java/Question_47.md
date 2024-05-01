# [LeetCode Records](../../README.md) - Question 47 Permutations II

### Attempt 1: Use three loops and two HashSet
```java
class Solution {
    public List<List<Integer>> permuteUnique(int[] nums) {
        Set<List<Integer>> result = new HashSet<>();

        // First element
        List<Integer> firstList = new LinkedList<>();
        firstList.add(nums[0]);
        result.add(firstList);

        // Loop for each element
        for (int i = 1; i < nums.length; i++) {
            Set<List<Integer>> tempResult = new HashSet<>();

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

        return result.stream().toList();
    }
}
```
- Runtime: 9 ms (Beats: 28.79%)
- Memory: 45.34 MB (Beats: 14.87%)

<br>
