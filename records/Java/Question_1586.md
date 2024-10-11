# [LeetCode Records](../../README.md) - Question 1586 Binary Search Tree Iterator II

### Attempt 1: Convert the Tree to an ArrayList
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
class BSTIterator {

    private List<Integer> list;
    private int currIndex;
    private int size;

    public BSTIterator(TreeNode root) {
        list = new ArrayList<>();
        currIndex = -1;

        addNodeToList(root);
        size = list.size();
    }

    private void addNodeToList(TreeNode root) {
        if (root == null) {
            return;
        }

        addNodeToList(root.left);
        list.add(root.val);
        addNodeToList(root.right);
    }
    
    public boolean hasNext() {
        return currIndex + 1 < size;
    }
    
    public int next() {
        currIndex++;
        return list.get(currIndex);
    }
    
    public boolean hasPrev() {
        return currIndex - 1 >= 0;
    }
    
    public int prev() {
        currIndex--;
        return list.get(currIndex);
    }
}

/**
 * Your BSTIterator object will be instantiated and called as such:
 * BSTIterator obj = new BSTIterator(root);
 * boolean param_1 = obj.hasNext();
 * int param_2 = obj.next();
 * boolean param_3 = obj.hasPrev();
 * int param_4 = obj.prev();
 */
```
- Runtime: 71 ms (Beats: 100.00%)
- Memory: 68.79 MB (Beats: 54.46%)

<br>
