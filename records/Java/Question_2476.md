# [LeetCode Records](../../README.md) - Question 2476 Closest Nodes Queries in a Binary Search Tree

### Attempt 1: Convert the binary search tree to a sorted arr and use binary search to find the query
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

    private int[] arr;

    public List<List<Integer>> closestNodes(TreeNode root, List<Integer> queries) {
        List<Integer> numList = new ArrayList<>();
        addNumsToList(numList, root);

        arr = new int[numList.size()];
        int i = 0;
        for (int num : numList) {
            arr[i] = num;
            i++;
        }

        List<List<Integer>> ans = new ArrayList<>(queries.size());
        for (int query : queries) {
            int minMax = arr[0] > query ? -1 : getMinMaxOrMaxMin(query, true);
            int maxMin = arr[arr.length - 1] < query ? -1 : getMinMaxOrMaxMin(query, false);
            ans.add(List.of(minMax, maxMin));
        }

        return ans;
    }

    private void addNumsToList(List<Integer> numList, TreeNode root) {
        if (root != null) {
            addNumsToList(numList, root.left);
            numList.addLast(root.val);
            addNumsToList(numList, root.right);
        }
    }

    private int getMinMaxOrMaxMin(int query, boolean isMinMax) {
        int min = 0;
        int max = arr.length - 1;
        while (min <= max) {
            int mid = min + (max - min) / 2;
            if (arr[mid] == query) {
                return query;
            } else if (query < arr[mid]) {
                max = mid - 1;
            } else {
                min = mid + 1;
            }
        }

        return isMinMax ? arr[min - 1] : arr[min];
    }
}
```
- Runtime: 77 ms (Beats: 76.88%)
- Memory: 88.54 MB (Beats: 87.39%)

<br>
