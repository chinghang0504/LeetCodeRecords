# [LeetCode Records](../../README.md) - Question 707 Design Linked List

### Attempt 1: Create a class Node that stores the previous and the next nodes
```java
class MyLinkedList {

    class Node {

        int val;
        Node prev;
        Node next;

        Node (int val) {
            this.val = val;
            this.prev = null;
            this.next = null;
        }

        Node (int val, Node prev, Node next) {
            this.val = val;
            this.prev = prev;
            this.next = next;
        }
    }

    private int size;
    private Node head;
    private Node tail;

    public MyLinkedList() {
        size = 0;
        head = null;
        tail = null;
    }
    
    public int get(int index) {
        if (index >= size) {
            return -1;
        }

        Node curr = head;
        for (int i = 0; i < index; i++) {
            curr = curr.next;
        }

        return curr.val;
    }
    
    public void addAtHead(int val) {
        Node node = new Node(val);

        if (size == 0) {
            tail = node;
        } else {
            node.next = head;
            head.prev = node;
        }

        head = node;
        size++;
    }
    
    public void addAtTail(int val) {
        Node node = new Node(val);

        if (size == 0) {
            head = node;
        } else {
            tail.next = node;
            node.prev = tail;
        }

        tail = node;
        size++;
    }
    
    public void addAtIndex(int index, int val) {
        if (index > size) {
            return;
        } else if (index == 0) {
            addAtHead(val);
            return;
        } else if (index == size) {
            addAtTail(val);
            return;
        }

        Node first = head;
        for (int i = 0; i < index - 1; i++) {
            first = first.next;
        }

        Node third = first.next;
        Node second = new Node(val, first, third);
        first.next = second;
        third.prev = second;
        size++;
    }
    
    public void deleteAtIndex(int index) {
        if (index >= size) {
            return;
        }

        if (index == 0) {
            if (size == 1) {
                head = null;
                tail = null;
            } else {
                head = head.next;
                head.prev = null;
            }
        } else if (index == size - 1) {
            tail = tail.prev;
            tail.next = null;
        } else {
            Node second = head;
            for (int i = 0; i < index; i++) {
                second = second.next;
            }

            Node first = second.prev;
            Node third = second.next;
            first.next = third;
            third.prev = first;
        }

        size--;
    }
}

/**
 * Your MyLinkedList object will be instantiated and called as such:
 * MyLinkedList obj = new MyLinkedList();
 * int param_1 = obj.get(index);
 * obj.addAtHead(val);
 * obj.addAtTail(val);
 * obj.addAtIndex(index,val);
 * obj.deleteAtIndex(index);
 */
```
- Runtime: 7 ms (Beats: 85.92%)
- Memory: 45.28 MB (Beats: 81.46%)

<br>
