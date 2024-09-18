# [LeetCode Records](../../README.md) - Question 1381 Design a Stack With Increment Operation

### Attempt 1: Use a LinkedList as a container
```java
class CustomStack {

    private List<Integer> list;
    private int maxSize;

    public CustomStack(int maxSize) {
        this.list = new LinkedList<>();
        this.maxSize = maxSize;
    }
    
    public void push(int x) {
        if (list.size() < maxSize) {
            list.addLast(x);
        }
    }
    
    public int pop() {
        return list.size() > 0 ? list.removeLast() : -1;
    }
    
    public void increment(int k, int val) {
        int size = Math.min(k, list.size());

        for (int i = 0; i < size; i++) {
            int prevVal = list.get(i);
            list.set(i, prevVal + val);
        }
    }
}

/**
 * Your CustomStack object will be instantiated and called as such:
 * CustomStack obj = new CustomStack(maxSize);
 * obj.push(x);
 * int param_2 = obj.pop();
 * obj.increment(k,val);
 */
```
- Runtime: 174 ms (Beats: 6.03%)
- Memory: 46.28 MB (Beats: 9.74%)

<br>

### Attempt 2: Use an int[] as a container
```java
class CustomStack {

    private int[] arr;
    private int currSize;
    private int maxSize; 

    public CustomStack(int maxSize) {
        this.arr = new int[maxSize];
        this.currSize = 0;
        this.maxSize = maxSize;
    }
    
    public void push(int x) {
        if (currSize < maxSize) {
            arr[currSize] = x;
            currSize++;
        }
    }
    
    public int pop() {
        if (currSize > 0) {
            currSize--;
            return arr[currSize];
        }

        return -1;
    }
    
    public void increment(int k, int val) {
        int minSize = Math.min(k, currSize);

        for (int i = 0; i < minSize; i++) {
            arr[i] += val;
        }
    }
}

/**
 * Your CustomStack object will be instantiated and called as such:
 * CustomStack obj = new CustomStack(maxSize);
 * obj.push(x);
 * int param_2 = obj.pop();
 * obj.increment(k,val);
 */
```
- Runtime: 5 ms (Beats: 94.05%)
- Memory: 45.31 MB (Beats: 73.18%)

<br>
