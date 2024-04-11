# [LeetCode Records](../README.md) - Question 117 Populating Next Right Pointers in Each Node II

### Attempt 1: Use an ArrayList to save the next level of nodes
```java
class Solution {
    public Node connect(Node root) {
        if (root == null) {
            return null;
        }

        List<Node> prevNodes = new ArrayList<>();
        prevNodes.add(root);
        
        while (!prevNodes.isEmpty()) {
            List<Node> nodes = new ArrayList<>();

            int size = prevNodes.size();
            Node curr = prevNodes.get(0);
            for (int i = 0; i < size - 1; i++) {
                Node next = prevNodes.get(i + 1);

                curr.next = next;
                if (curr.left != null) {
                    nodes.add(curr.left);
                }
                if (curr.right != null) {
                    nodes.add(curr.right);
                }

                curr = next;
            }
            curr.next = null;
            if (curr.left != null) {
                nodes.add(curr.left);
            }
            if (curr.right != null) {
                nodes.add(curr.right);
            }
            
            prevNodes = nodes;
        }

        return root;
    }
}
```
- Runtime: 1 ms (Beats: 69.88%)
- Memory: 44.28 MB (Beats: 35.77%)

<br>
