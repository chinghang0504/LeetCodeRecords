# [LeetCode Records](../../README.md) - Question 1670 Design Front Middle Back Queue

### Attempt 1: Use a LinkedList to store the values
```java
class FrontMiddleBackQueue {

    private List<Integer> container;

    public FrontMiddleBackQueue() {
        container = new LinkedList<>();
    }
    
    public void pushFront(int val) {
        container.addFirst(val);
    }
    
    public void pushMiddle(int val) {
        container.add(container.size() / 2, val);
    }
    
    public void pushBack(int val) {
        container.addLast(val);
    }
    
    public int popFront() {
        return container.isEmpty() ? -1 : container.removeFirst();
    }
    
    public int popMiddle() {
        if (container.isEmpty()) {
            return -1;
        }

        int size = container.size();
        int index = size % 2 == 0 ? size / 2 - 1 : size / 2;
        return container.remove(index);
    }
    
    public int popBack() {
        return container.isEmpty() ? -1 : container.removeLast();
    }
}

/**
 * Your FrontMiddleBackQueue object will be instantiated and called as such:
 * FrontMiddleBackQueue obj = new FrontMiddleBackQueue();
 * obj.pushFront(val);
 * obj.pushMiddle(val);
 * obj.pushBack(val);
 * int param_4 = obj.popFront();
 * int param_5 = obj.popMiddle();
 * int param_6 = obj.popBack();
 */
```
- Runtime: 8 ms (Beats: 34.35%)
- Memory: 45.20 MB (Beats: 79.53%)

<br>
