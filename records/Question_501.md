# [LeetCode Records](../README.md) - Question 501 Find Mode in Binary Search Tree

### Attempt 1: Use a HashMap
```java
class Solution {

    private Map<Integer, Integer> map;

    public int[] findMode(TreeNode root) {
        map = new HashMap<>();

        findModeRecursion(root);

        int max = map.values().stream().max(Integer::compareTo).get();
        
        return map.entrySet().stream()
                .filter(i -> i.getValue() == max)
                .map(i -> i.getKey())
                .mapToInt(i -> i)
                .toArray();
    }

    private void findModeRecursion(TreeNode root) {
        if (root == null) {
            return;
        } else if (root.left == null && root.right == null) {
            map.merge(root.val, 1, Integer::sum);
            return;
        }

        map.merge(root.val, 1, Integer::sum);
        findModeRecursion(root.left);
        findModeRecursion(root.right);
    }
}
```
- Runtime: 9 ms (Beats: 15.95%)
- Memory: 45.73 MB (Beats: 6.10%)

<br>
