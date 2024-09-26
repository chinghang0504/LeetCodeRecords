# [LeetCode Records](../../README.md) - Question 78 Subsets

### Attempt 1: Use a recursion to add a new number to the previous list
```java
class Solution {
    public List<List<Integer>> subsets(int[] nums) {
        List<List<Integer>> ans = new ArrayList<>();
        List<Integer> emptyList = List.of();
        ans.add(emptyList);

        generateSubsets(nums, ans, emptyList, 0);
        
        return ans;
    }

    private void generateSubsets(int[] nums, List<List<Integer>> ans, List<Integer> prevList, int startIndex) {
        if (startIndex >= nums.length) {
            return;
        }

        for (int i = startIndex; i < nums.length; i++) {
            List<Integer> copyList = new ArrayList<>(prevList);
            copyList.add(nums[i]);
            ans.add(copyList);

            generateSubsets(nums, ans, copyList, i + 1);
        }
    }
}
```
- Runtime: 1 ms (Beats: 53.56%)
- Memory: 42.49 MB (Beats: 84.46%)

<br>
