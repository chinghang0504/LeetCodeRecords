# [LeetCode Records](../../README.md) - Question 508 Most Frequent Subtree Sum

### Attempt 1: Use a HashMap to store the sum and frequency key-value pairs
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

    private Map<Integer, Integer> map;

    public int[] findFrequentTreeSum(TreeNode root) {
        map = new HashMap<>();

        findFrequentTreeSumRecursion(root);
        
        List<Map.Entry<Integer, Integer>> list = new ArrayList<>(map.entrySet());
        int maxFreq = 0;
        int[] maxFreqArr = new int[10000];
        int size = 0;

        for (Map.Entry<Integer, Integer> entry : list) {
            int freq = entry.getValue();
            if (freq > maxFreq) {
                maxFreq = freq;
                maxFreqArr[0] = entry.getKey();
                size = 1;
            } else if (freq == maxFreq) {
                maxFreqArr[size] = entry.getKey();
                size++;
            }
        }

        return Arrays.copyOf(maxFreqArr, size);
    }

    private int findFrequentTreeSumRecursion(TreeNode root) {
        if (root == null) {
            return 0;
        } else if (root.left == null && root.right == null) {
            map.merge(root.val, 1, Integer::sum);
            return root.val;
        }

        int sum = root.val;
        sum += findFrequentTreeSumRecursion(root.left);
        sum += findFrequentTreeSumRecursion(root.right);
        map.merge(sum, 1, Integer::sum);

        return sum;
    }
}
```
- Runtime: 6 ms (Beats: 41.28%)
- Memory: 44.34 MB (Beats: 99.52%)

<br>
