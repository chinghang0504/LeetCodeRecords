# [LeetCode Records](../../README.md) - Question 863 All Nodes Distance K in Binary Tree

### Attempt 1: Use a HashMap to store the node value and its path key-value pairs
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
class Solution {
    public List<Integer> distanceK(TreeNode root, TreeNode target, int k) {
        Map<Integer, String> valToPathMap = new HashMap<>();
        getPaths(valToPathMap, new StringBuilder(), root);

        char[] targetArr = valToPathMap.get(target.val).toCharArray();
        int rootToTarget = targetArr.length;

        List<Integer> ans = new ArrayList<>();
        for (Map.Entry<Integer, String> entry : valToPathMap.entrySet()) {
            char[] nodeArr = entry.getValue().toCharArray();
            int targetIndex = 0;
            int nodeIndex = 0;
            while (targetIndex < targetArr.length && nodeIndex < nodeArr.length && targetArr[targetIndex] == nodeArr[nodeIndex]) {
                targetIndex++;
                nodeIndex++;
            }

            int distance = targetIndex == 0 ? rootToTarget + nodeArr.length : targetArr.length - targetIndex + nodeArr.length - nodeIndex;
            if (distance == k) {
                ans.add(entry.getKey());
            }
        }


        return ans;
    }

    private void getPaths(Map<Integer, String> valToPathMap, StringBuilder stringBuilder, TreeNode root) {
        valToPathMap.put(root.val, stringBuilder.toString());

        if (root.left != null) {
            stringBuilder.append('L');
            getPaths(valToPathMap, stringBuilder, root.left);
            stringBuilder.deleteCharAt(stringBuilder.length() - 1);
        }

        if (root.right != null) {
            stringBuilder.append('R');
            getPaths(valToPathMap, stringBuilder, root.right);
            stringBuilder.deleteCharAt(stringBuilder.length() - 1);
        }
    }
}
```
- Runtime: 13 ms (Beats: 68.42%)
- Memory: 42.38 MB (Beats: 82.84%)

<br>
