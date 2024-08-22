# [LeetCode Records](../../README.md) - Question 3263 Convert Doubly Linked List to Array I

### Attempt 1: Create an int[] with the size of the maximum length
```java
class Solution {
    public int[] toArray(Node head) {
        int[] arr = new int[50];
        int size = 0;

        Node curr = head;
        while (curr != null) {
            arr[size] = curr.val;
            size++;
            curr = curr.next;
        }

        return Arrays.copyOf(arr, size);
    }
}
```
- Runtime: 1 ms (Beats: 100.00%)
- Memory: 44.87 MB (Beats: 100.00%)

<br>
