# [LeetCode Records](../../README.md) - Question 872 Leaf-Similar Trees

### Attempt 1: Use the recursion to get the leaf value sequence
```java
class Solution {
    public boolean leafSimilar(TreeNode root1, TreeNode root2) {
        List<Integer> list1 = new ArrayList<>();
        List<Integer> list2 = new ArrayList<>();

        getLeafValueSequence(root1, list1);
        getLeafValueSequence(root2, list2);

        return list1.equals(list2);
    }

    private void getLeafValueSequence(TreeNode root, List<Integer> list) {
        if (root == null) {
            return;
        } else if (root.left == null && root.right == null) {
            list.add(root.val);
            return;
        }

        getLeafValueSequence(root.left, list);
        getLeafValueSequence(root.right, list);
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 41.07 MB (Beats: 84.48%)

<br>
