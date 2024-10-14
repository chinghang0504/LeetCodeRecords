# [LeetCode Records](../../README.md) - Question 919 Complete Binary Tree Inserter

### Attempt 1: Use an ArrayList to store the parent nodes and an ArrayList to store the child nodes
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
class CBTInserter {

    private TreeNode root;
    private List<TreeNode> list;
    private List<TreeNode> nextList;

    public CBTInserter(TreeNode root) {
        this.root = root;

        list = new ArrayList<>();
        list.add(root);
        nextList = new ArrayList<>();

        while (true) {
            for (TreeNode node : list) {
                if (node.left != null) {
                    nextList.add(node.left);
                } else {
                    break;
                }
                
                if (node.right != null) {
                    nextList.add(node.right);
                } else {
                    break;
                }
            }

            if (list.size() * 2 == nextList.size()) {
                list = nextList;
                nextList = new ArrayList<>();
            } else {
                break;
            }
        }
    }
    
    public int insert(int val) {
        TreeNode parent = null;

        for (TreeNode node : list) {
            if (node.left == null) {
                TreeNode nextNode = new TreeNode(val);
                node.left = nextNode;
                nextList.add(nextNode);
                parent = node;
                break;
            } else if (node.right == null) {
                TreeNode nextNode = new TreeNode(val);
                node.right = nextNode;
                nextList.add(nextNode);
                parent = node;
                break;
            }
        }

        if (parent != null) {
            return parent.val;
        }

        list = nextList;
        nextList = new ArrayList<>();
        parent = list.get(0);
        TreeNode nextNode = new TreeNode(val);
        parent.left = nextNode;
        nextList.add(nextNode);

        return parent.val;
    }
    
    public TreeNode get_root() {
        return root;
    }
}

/**
 * Your CBTInserter object will be instantiated and called as such:
 * CBTInserter obj = new CBTInserter(root);
 * int param_1 = obj.insert(val);
 * TreeNode param_2 = obj.get_root();
 */
```
- Runtime: 16 ms (Beats: 22.04%)
- Memory: 44.49 MB (Beats: 91.05%)

<br>
