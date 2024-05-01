# [LeetCode Records](../../README.md) - Question 225 Implement Stack using Queues

### Attempt 1: Use a ArrayList
```java
class MyStack {

    List<Integer> list;

    public MyStack() {
        this.list = new ArrayList<>();
    }
    
    public void push(int x) {
        this.list.addLast(x);
    }
    
    public int pop() {
        return this.list.removeLast();
    }
    
    public int top() {
        return this.list.getLast();
    }
    
    public boolean empty() {
        return this.list.isEmpty();
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 40.99 MB (Beats: 86.21%)

<br>
