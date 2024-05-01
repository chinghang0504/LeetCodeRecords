# [LeetCode Records](../../README.md) - Question 109 Convert Sorted List to Binary Search Tree

### Attempt 1: Find the middle node and then use recursion
```java
class Solution {
    public TreeNode sortedListToBST(ListNode head) {
        // Empty list
        if (head == null) {
            return null;
        }

        // Count the number of nodes
        ListNode curr = head;
        int count = 0;
        for (; curr != null; count++) {
            curr = curr.next;
        }

        return sortedListToBSTRecursion(head, count);
    }

    private TreeNode sortedListToBSTRecursion(ListNode head, int count) {
        // One node list
        if (count == 1) {
            return new TreeNode(head.val);
        } 
        // Two node list
        else if (count == 2) {
            TreeNode left = new TreeNode(head.val);
            return new TreeNode(head.next.val, left, null);
        }

        // Get the position of the middle node
        int middle = count / 2;

        // Get the node that points to before the middle node
        ListNode dummy = new ListNode(0, head);
        ListNode curr1 = dummy;
        for (int i = 0; i < middle; i++) {
            curr1 = curr1.next;
        }

        // Get the middle node
        ListNode curr2 = curr1.next;

        // Get the node that points to after the middle node
        ListNode curr3 = curr2.next;

        // Get the root, left, right nodes
        TreeNode root = new TreeNode(curr2.val);
        root.left = sortedListToBSTRecursion(dummy.next, middle);
        root.right = sortedListToBSTRecursion(curr3, count - middle - 1);
        
        return root;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 44.16 MB (Beats: 97.47%)

<br>
