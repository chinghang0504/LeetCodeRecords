# [LeetCode Records](../../README.md) - Question 1367 Linked List in Binary Tree

### Attempt 1: Use a recusive function to check every node in the linked list
```java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode() {}
 *     ListNode(int val) { this.val = val; }
 *     ListNode(int val, ListNode next) { this.val = val; this.next = next; }
 * }
 */
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
    public boolean isSubPath(ListNode head, TreeNode root) {
        if (root == null) {
            return false;
        } else if (isSubPathThoughNodes(head, root)) {
            return true;
        }
        
        if (isSubPath(head, root.left)) {
            return true;
        } else if (isSubPath(head, root.right)) {
            return true;
        }

        return false;
    }

    private boolean isSubPathThoughNodes(ListNode node, TreeNode root) {
        if (node == null) {
            return true;
        } else if (root == null) {
            return false;
        } else if (node.val != root.val) {
            return false;
        }

        if (isSubPathThoughNodes(node.next, root.left)) {
            return true;
        } else if (isSubPathThoughNodes(node.next, root.right)) {
            return true;
        }

        return false;
    }
}
```
- Runtime: 1 ms (Beats: 99.50%)
- Memory: 45.14 MB (Beats: 29.06%)

<br>
