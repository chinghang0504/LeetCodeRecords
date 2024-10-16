# [LeetCode Records](../../README.md) - Question 988 Smallest String Starting From Leaf

### Attempt 1: Return multiple strings if there is not enough information to judge
```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 * int val;
 * TreeNode left;
 * TreeNode right;
 * TreeNode() {}
 * TreeNode(int val) { this.val = val; }
 * TreeNode(int val, TreeNode left, TreeNode right) {
 * this.val = val;
 * this.left = left;
 * this.right = right;
 * }
 * }
 */
class Solution {
    public String smallestFromLeaf(TreeNode root) {
        List<String> list = smallestFromLeafRecursion(root);
        int size = list.size();
        if (size == 1) {
            return list.get(0);
        } else {
            String smallestString = list.get(0);
            
            for (int i = 1; i < size; i++) {
                String str = list.get(i);
                if (str.compareTo(smallestString) == -1) {
                    smallestString = str;
                }
            }

            return smallestString;
        }
    }

    private List<String> smallestFromLeafRecursion(TreeNode root) {
        List<String> list = new ArrayList<>();
        if (root.left != null) {
            list.addAll(smallestFromLeafRecursion(root.left));
        }
        if (root.right != null) {
            list.addAll(smallestFromLeafRecursion(root.right));
        }

        char ch = (char)(root.val + 'a');
        int size = list.size();
        if (size == 0) {
            list.add("" + ch);
            return list;
        } else if (size == 1) {
            list.set(0, list.get(0) + ch);
            return list;
        } else {
            List<String> nextList = new ArrayList<>();
            nextList.add(list.get(0) + ch);

            for (int i = 1; i < size; i++) {
                String str = list.get(i) + ch;
                int score = compareStrings(nextList.get(0), str);
                if (score == 1) {
                    nextList.clear();
                    nextList.add(str);
                } else if (score == 0) {
                    nextList.add(str);
                }
            }

            return nextList;
        }
    }

    private int compareStrings(String s1, String s2) {
        char[] arr1 = s1.toCharArray();
        char[] arr2 = s2.toCharArray();
        int minSize = Math.min(arr1.length, arr2.length);

        for (int i = 0; i < minSize; i++) {
            if (arr1[i] < arr2[i]) {
                return -1;
            } else if (arr1[i] > arr2[i]) {
                return 1;
            }
        }

        return 0;
    }
}
```
- Runtime: 17 ms (Beats: 6.03%)
- Memory: 46.21 MB (Beats: 8.39%)

<br>
