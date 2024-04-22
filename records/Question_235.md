# [LeetCode Records](../README.md) - Question 235 Lowest Common Ancestor of a Binary Search Tree

### Attempt 1: Get both path of the nodes
```java
class Solution {
    public TreeNode lowestCommonAncestor(TreeNode root, TreeNode p, TreeNode q) {
        List<TreeNode> pList = new ArrayList<>();
        List<TreeNode> qList = new ArrayList<>();

        updatePathRecursion(root, p, pList);
        updatePathRecursion(root, q, qList);

        Iterator<TreeNode> pIterator = pList.iterator();
        Iterator<TreeNode> qIterator = qList.iterator();
        TreeNode result = null;

        while (pIterator.hasNext() && qIterator.hasNext()) {
            TreeNode pNode = pIterator.next();
            TreeNode qNode = qIterator.next();
            if (pNode == qNode) {
                result = pNode;
            } else {
                break;
            }
        }

        return result;
    }

    private void updatePathRecursion(TreeNode root, TreeNode target, List<TreeNode> list) {
        list.add(root);
        
        if (root == target) {
            return;
        }

        if (target.val < root.val) {
            updatePathRecursion(root.left, target, list);
        } else {
            updatePathRecursion(root.right, target, list);
        }
    }
}
```
- Runtime: 6 ms (Beats: 38.30%)
- Memory: 45.17 MB (Beats: 23.83%)

<br>

### Attempt 2: Compare to the root value
```java
class Solution {
    public TreeNode lowestCommonAncestor(TreeNode root, TreeNode p, TreeNode q) {
        return lowestCommonAncestorRecursion(root, p, q);
    }

    private TreeNode lowestCommonAncestorRecursion(TreeNode root, TreeNode p, TreeNode q) {
        if (root.val == p.val || root.val == q.val) {
            return root;
        } else if (root.val > p.val && root.val > q.val) {
            return lowestCommonAncestorRecursion(root.left, p, q);
        } else if (root.val < p.val && root.val < q.val) {
                return lowestCommonAncestorRecursion(root.right, p, q);
        } else {
            return root;
        }
    }
}
```
- Runtime: 5 ms (Beats: 100.00%)
- Memory: 44.78 MB (Beats: 74.25%)

<br>
