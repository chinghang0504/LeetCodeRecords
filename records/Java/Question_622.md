# [LeetCode Records](../../README.md) - Question 622 Design Circular Queue

### Attempt 1: Use an int[] to implement a circular queue
```java
class MyCircularQueue {

    private int capacity;
    private int size;
    private int[] container;
    private int startIndex;
    private int endIndex;

    public MyCircularQueue(int k) {
        capacity = k;
        size = 0;
        container = new int[k];
        startIndex = 0;
        endIndex = 0;
    }
    
    public boolean enQueue(int value) {
        if (size == capacity) {
            return false;
        }

        size++;
        container[endIndex] = value;
        endIndex = (endIndex + 1) % capacity;
        return true;
    }
    
    public boolean deQueue() {
        if (size == 0) {
            return false;
        }

        size--;
        startIndex = (startIndex + 1) % capacity;
        return true;
    }
    
    public int Front() {
        if (size == 0) {
            return -1;
        }

        return container[startIndex];
    }
    
    public int Rear() {
        if (size == 0) {
            return -1;
        }

        int index = endIndex == 0 ? capacity - 1 : endIndex - 1;
        return container[index];
    }
    
    public boolean isEmpty() {
        return size == 0;
    }
    
    public boolean isFull() {
        return size == capacity;
    }
}

/**
 * Your MyCircularQueue object will be instantiated and called as such:
 * MyCircularQueue obj = new MyCircularQueue(k);
 * boolean param_1 = obj.enQueue(value);
 * boolean param_2 = obj.deQueue();
 * int param_3 = obj.Front();
 * int param_4 = obj.Rear();
 * boolean param_5 = obj.isEmpty();
 * boolean param_6 = obj.isFull();
 */
```
- Runtime: 4 ms (Beats: 100.00%)
- Memory: 44.62 MB (Beats: 49.66%)

<br>
