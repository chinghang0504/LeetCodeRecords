# [LeetCode Records](../../README.md) - Question 655 Print Binary Tree

### Attempt 1: Use a HashMap to store the depth and its node list key-value pairs
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

    private Map<Integer, List<int[]>> depthToNodeListMap;
    private int maxDepth;
    private int n;

    public List<List<String>> printTree(TreeNode root) {
        depthToNodeListMap = new HashMap<>();
        maxDepth = 0;
        n = 1;

        addNodesToMap(root, 0, 0);

        for (int i = 0; i < maxDepth + 1; i++) {
            n *= 2;
        }
        n--;

        List<List<String>> ans = new ArrayList<>();
        for (int i = 0; i < maxDepth + 1; i++) {
            List<String> row = new ArrayList<>();
            for (int j = 0; j < n; j++) {
                row.add("");
            }
            ans.add(row);
        }

        int startIndex = 0;
        int space = 2;
        for (int i = maxDepth; i >= 0; i--) {
            List<String> row = ans.get(i);
            List<int[]> nodeList = depthToNodeListMap.get(i);
            if (nodeList == null) {
                continue;
            }

            for (int[] node : nodeList) {
                int index = startIndex + space * node[0];
                row.set(index, String.valueOf(node[1]));
            }

            startIndex = (startIndex + 1) * 2 - 1;
            space *= 2;
        }

        return ans;
    }

    private void addNodesToMap(TreeNode root, int depth, int currIndex) {
        if (root == null) {
            return;
        }

        maxDepth = Math.max(maxDepth, depth);

        List<int[]> nodeList = depthToNodeListMap.get(depth);
        if (nodeList == null) {
            nodeList = new ArrayList<>();
            depthToNodeListMap.put(depth, nodeList);
        }
        nodeList.add(new int[]{ currIndex, root.val});

        addNodesToMap(root.left, depth + 1, currIndex + currIndex);
        addNodesToMap(root.right, depth + 1, currIndex + currIndex + 1);
    }
}
```
- Runtime: 1 ms (Beats: 87.38%)
- Memory: 43.71 MB (Beats: 55.69%)

<br>
