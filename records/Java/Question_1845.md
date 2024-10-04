# [LeetCode Records](../../README.md) - Question 1845 Seat Reservation Manager

### Attempt 1: Use a PriorityQueue to store the seat numbers
```java
class SeatManager {

    private PriorityQueue<Integer> priorityQueue;

    public SeatManager(int n) {
        priorityQueue = new PriorityQueue<>();
        for (int i = 1; i <= n; i++) {
            priorityQueue.add(i);
        }
    }
    
    public int reserve() {
        return priorityQueue.remove();
    }
    
    public void unreserve(int seatNumber) {
        priorityQueue.add(seatNumber);
    }
}

/**
 * Your SeatManager object will be instantiated and called as such:
 * SeatManager obj = new SeatManager(n);
 * int param_1 = obj.reserve();
 * obj.unreserve(seatNumber);
 */
```
- Runtime: 87 ms (Beats: 68.60%)
- Memory: 88.76 MB (Beats: 67.25%)

<br>
