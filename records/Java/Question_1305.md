# [LeetCode Records](../../README.md) - Question 1305 All Elements in Two Binary Search Trees

### Attempt 1: Store all the element values in the list and use Collections.sort() to sort the list
```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode() {}
 *     TreeNode(int val) { this.val = val; }
 *     TreeNode(int val, TreeNode left, TreeNode right) {
 *         this.val = val;
 *         this.left = left;
 *         this.right = right;
 *     }
 * }
 */
class Solution {

    private List<Integer> list;

    public List<Integer> getAllElements(TreeNode root1, TreeNode root2) {
        list = new ArrayList<>();
        
        getAllElementsFromTree(root1);
        getAllElementsFromTree(root2);

        Collections.sort(list);

        return list;
    }

    private void getAllElementsFromTree(TreeNode root) {
        if (root != null) {
            list.add(root.val);
        } else {
            return;
        }

        getAllElementsFromTree(root.left);
        getAllElementsFromTree(root.right);
    }
}
```
- Runtime: 17 ms (Beats: 76.34%)
- Memory: 45.71 MB (Beats: 95.90%)

<br>
