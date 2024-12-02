# [LeetCode Records](../../README.md) - Question 708 Insert into a Sorted Circular Linked List

### Attempt 1: Track the node with the highest value
```java
/*
// Definition for a Node.
class Node {
    public int val;
    public Node next;

    public Node() {}

    public Node(int _val) {
        val = _val;
    }

    public Node(int _val, Node _next) {
        val = _val;
        next = _next;
    }
};
*/

class Solution {
    public Node insert(Node head, int insertVal) {
        if (head == null) {
            Node node = new Node(insertVal);
            node.next = node;
            return node;
        }

        Node highestNode = new Node(Integer.MIN_VALUE);
        Node curr1 = head;
        Node curr2 = head.next;
        do {
            if (curr1.val <= insertVal && insertVal <= curr2.val) {
                Node node = new Node(insertVal);
                node.next = curr2;
                curr1.next = node;
                return head;
            } else if (curr2.val >= highestNode.val) {
                if (curr2.val > highestNode.val || curr2.next.val < curr2.val) {
                    highestNode = curr2;
                }
            }

            curr1 = curr2;
            curr2 = curr2.next;
        } while (curr2 != head.next);

        Node node = new Node(insertVal);
        node.next = highestNode.next;
        highestNode.next = node;

        return head;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 42.85 MB (Beats: 44.27%)

<br>
