# [LeetCode Records](../../README.md) - Question 2046 Sort Linked List Already Sorted Using Absolute Values

### Attempt 1: Use a ListNode[] to store nodes and a int[] to store numbers
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
class Solution {
    public ListNode sortLinkedList(ListNode head) {
        ListNode[] nodes = new ListNode[100000];
        int[] nums = new int[100000];
        int size = 0;

        ListNode curr = head;
        while (curr != null) {
            nodes[size] = curr;
            nums[size] = curr.val;
            size++;
            curr = curr.next;
        }
        
        nums = Arrays.copyOf(nums, size);
        Arrays.sort(nums);

        for (int i = 0; i < size; i++) {
            nodes[i].val = nums[i];
        }

        return head;
    }
}
```
- Runtime: 11 ms (Beats: 9.84%)
- Memory: 59.39 MB (Beats: 96.72%)

<br>
