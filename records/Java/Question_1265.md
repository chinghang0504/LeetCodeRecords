# [LeetCode Records](../../README.md) - Question 1265 Print Immutable Linked List in Reverse

### Attempt 1: Use an array to store nodes
```java
class Solution {
    public void printLinkedListInReverse(ImmutableListNode head) {
        ImmutableListNode[] nodes = new ImmutableListNode[1000];
        int size = 0;
        
        ImmutableListNode curr = head;
        while (curr != null) {
            nodes[size] = curr;
            size++;
            curr = curr.getNext();
        }

        for (int i = size - 1; i >= 0; i--) {
            nodes[i].printValue();
        }
    }
}
```
- Runtime: 1 ms (Beats: 43.56%)
- Memory: 41.97 MB (Beats: 48.11%)

<br>

### Attempt 2: Use recursion
```java
class Solution {
    public void printLinkedListInReverse(ImmutableListNode head) {
        ImmutableListNode next = head.getNext();
        if (next != null) {
            printLinkedListInReverse(next);
        }
        head.printValue();
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 42.23 MB (Beats: 9.47%)

<br>
