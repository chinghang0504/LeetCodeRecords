# [LeetCode Records](../README.md) - Question 138 Copy List with Random Pointer

### Attempt 1: Use two HashMap to record nodes
```java
class Solution {
    public Node copyRandomList(Node head) {
        Map<Node, Integer> orgSaved = new HashMap<>();
        Map<Integer, Node> copySaved = new HashMap<>();

        Node dummy = new Node(0);
        Node currCopy = dummy;

        Node currOrg = head;
        int index = 0;
        while (currOrg != null) {
            orgSaved.put(currOrg, index);

            Node copyNode = new Node(currOrg.val);
            copySaved.put(index, copyNode);

            currOrg = currOrg.next;
            currCopy.next = copyNode;
            currCopy = copyNode;
            index++;
        }

        currCopy = dummy.next;
        currOrg = head;
        while (currOrg != null) {
            Node randomNode = currOrg.random;
            if (randomNode != null) {
                currCopy.random = copySaved.get(orgSaved.get(randomNode));
            }

            currOrg = currOrg.next;
            currCopy = currCopy.next;
        }

        return dummy.next;
    }
}
```
- Runtime: 1 ms (Beats: 9.72%)
- Memory: 44.38 MB (Beats: 51.12%)

<br>
