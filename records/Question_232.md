# [LeetCode Records](../README.md) - Question 232 Implement Queue using Stacks

### Attempt 1: Use a LinkedList
```java
class MyQueue {

    List<Integer> list;

    public MyQueue() {
        this.list = new LinkedList<>();
    }

    public void push(int x) {
        this.list.addLast(x);
    }

    public int pop() {
        return this.list.removeFirst();
    }

    public int peek() {
        return this.list.getFirst();
    }

    public boolean empty() {
        return this.list.isEmpty();
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 41.19 MB (Beats: 63.65%)

<br>
