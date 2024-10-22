# [LeetCode Records](../../README.md) - Question 155 Min Stack

### Attempt 1: Use an ArrayList to store the value and the current minimum value pairs
```java
class MinStack {

    private List<int[]> container;

    public MinStack() {
        container = new ArrayList<>();
    }
    
    public void push(int val) {
        if (container.isEmpty()) {
            container.addLast(new int[]{ val, val });
        } else {
            int[] lastItem = container.getLast();
            container.addLast(new int[]{ val, Math.min(val, lastItem[1]) });
        }
    }
    
    public void pop() {
        container.removeLast();
    }
    
    public int top() {
        return container.getLast()[0];
    }
    
    public int getMin() {
        return container.getLast()[1];
    }
}

/**
 * Your MinStack object will be instantiated and called as such:
 * MinStack obj = new MinStack();
 * obj.push(val);
 * obj.pop();
 * int param_3 = obj.top();
 * int param_4 = obj.getMin();
 */
```
- Runtime: 4 ms (Beats: 96.96%)
- Memory: 44.76 MB (Beats: 58.85%)

<br>
