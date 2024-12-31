# [LeetCode Records](../../README.md) - Question 297 Serialize and Deserialize Binary Tree

### Attempt 1: Use preorder traversal to add the node values
```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode(int x) { val = x; }
 * }
 */
public class Codec {

    // Encodes a tree to a single string.
    public String serialize(TreeNode root) {
        StringBuilder stringBuilder = new StringBuilder();
        addToStringBuilder(root, stringBuilder);

        return stringBuilder.toString();
    }

    private void addToStringBuilder(TreeNode node, StringBuilder stringBuilder) {
        if (node == null) {
            stringBuilder.append(" ,");
        } else {
            stringBuilder.append(node.val);
            stringBuilder.append(',');
            addToStringBuilder(node.left, stringBuilder);
            addToStringBuilder(node.right, stringBuilder);
        }
    }

    private int currIndex;

    // Decodes your encoded data to tree.
    public TreeNode deserialize(String data) {
        String[] splits = data.split(",");
        currIndex = 0;

        return generateTreeNode(splits);
    }

    private TreeNode generateTreeNode(String[] splits) {
        if (splits[currIndex].charAt(0) == ' ') {
            return null;
        }

        TreeNode node = new TreeNode(Integer.valueOf(splits[currIndex]));
        currIndex++;

        node.left = generateTreeNode(splits);
        currIndex++;

        node.right = generateTreeNode(splits);
        return node;
    }
}

// Your Codec object will be instantiated and called as such:
// Codec ser = new Codec();
// Codec deser = new Codec();
// TreeNode ans = deser.deserialize(ser.serialize(root));
```
- Runtime: 6 ms (Beats: 97.60%)
- Memory: 46.08 MB (Beats: 48.07%)

<br>
