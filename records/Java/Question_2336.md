# [LeetCode Records](../../README.md) - Question 2336 Smallest Number in Infinite Set

### Attempt 1: Use a priority queue to store the added numbers
```java
class SmallestInfiniteSet {

    private PriorityQueue<Integer> priorityQueue;
    private int currSmallest;

    public SmallestInfiniteSet() {
        priorityQueue = new PriorityQueue<>();
        currSmallest = 1;
    }
    
    public int popSmallest() {
        Integer firstNum = priorityQueue.poll();
        if (firstNum != null) {
            return firstNum;
        }

        return currSmallest++;
    }
    
    public void addBack(int num) {
        if (num < currSmallest && !priorityQueue.contains(num)) {
            priorityQueue.add(num);
        }
    }
}

/**
 * Your SmallestInfiniteSet object will be instantiated and called as such:
 * SmallestInfiniteSet obj = new SmallestInfiniteSet();
 * int param_1 = obj.popSmallest();
 * obj.addBack(num);
 */
```
- Runtime: 9 ms (Beats: 95.38%)
- Memory: 45.16 MB (Beats: 86.85%)

<br>
