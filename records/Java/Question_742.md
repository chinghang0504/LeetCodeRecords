# [LeetCode Records](../../README.md) - Question 742 Closest Leaf in a Binary Tree

### Attempt 1: Use an ArrayList to store the path of each leaf
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

    class Item {

        int val;
        String path;

        Item(int val, String path) {
            this.val = val;
            this.path = path;
        }
    }

    private List<Item> itemList;
    private String targetPath;
    private int k;

    public int findClosestLeaf(TreeNode root, int k) {
        itemList = new ArrayList<>();
        this.k = k;

        getItems(new StringBuilder(), root, k);
        if (itemList.isEmpty()) {
            return 0;
        }

        return getMinDistanceNode();
    }

    private void getItems(StringBuilder stringBuilder, TreeNode root, int k) {
        if (root.val == k) {
            targetPath = stringBuilder.toString();
        }

        if (root.left == null && root.right == null) {
            itemList.add(new Item(root.val, stringBuilder.toString()));
            return;
        }

        int len = stringBuilder.length();
        if (root.left != null) {
            stringBuilder.append('L');
            getItems(stringBuilder, root.left, k);
            stringBuilder.deleteCharAt(len);
        }

        if (root.right != null) {
            stringBuilder.append('R');
            getItems(stringBuilder, root.right, k);
            stringBuilder.deleteCharAt(len);
        }
    }

    private int getMinDistanceNode() {
        char[] arr1 = targetPath.toCharArray();
        int minDistance = Integer.MAX_VALUE;
        int minDistanceNode = 0;

        for (Item item : itemList) {
            char[] arr2 = item.path.toCharArray();
            int minSize = Math.min(arr1.length, arr2.length);
            int i = 0;
            while (i < minSize && arr1[i] == arr2[i]) {
                i++;
            }

            int distance = arr1.length + arr2.length;
            if (i != 0) {
                distance -= i + i;
            }
            if (distance < minDistance) {
                minDistance = distance;
                minDistanceNode = item.val;
            }
        }

        return minDistanceNode;
    }
}
```
- Runtime: 2 ms (Beats: 94.05%)
- Memory: 43.00 MB (Beats: 98.38%)

<br>
