# [LeetCode Records](../../README.md) - Question 1261 Find Elements in a Contaminated Binary Tree

### Attempt 1: Use a HashSet to store the values
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
class FindElements {

    private Set<Integer> set;

    public FindElements(TreeNode root) {
        set = new HashSet<>();
        setElementValue(root, 0);
    }

    private void setElementValue(TreeNode root, int val) {
        if (root == null) {
            return;
        }

        root.val = val;
        set.add(val);
        setElementValue(root.left, 2 * val + 1);
        setElementValue(root.right, 2 * val + 2);
    }
    
    public boolean find(int target) {
        return set.contains(target);
    }
}

/**
 * Your FindElements object will be instantiated and called as such:
 * FindElements obj = new FindElements(root);
 * boolean param_1 = obj.find(target);
 */
```
- Runtime: 20 ms (Beats: 98.58%)
- Memory: 47.58 MB (Beats: 34.09%)

<br>
