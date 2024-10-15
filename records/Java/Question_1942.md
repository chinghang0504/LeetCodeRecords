# [LeetCode Records](../../README.md) - Question 1942 The Number of the Smallest Unoccupied Chair

### Attempt 1: Use a PriorityQueue to record the chair numbers and a PriorityQueue to record the occupied chair numbers
```java
class Solution {
    public int smallestChair(int[][] times, int targetFriend) {
        int targetArrivalTime = times[targetFriend][0];
        Arrays.sort(times, (t1, t2) -> t1[0] - t2[0]);

        PriorityQueue<Integer> chairQueue = new PriorityQueue<>();
        for (int i = 0; i < times.length; i++) {
            chairQueue.add(i);
        }

        PriorityQueue<int[]> occupiedQueue = new PriorityQueue<>((o1, o2) -> o1[0] - o2[0]);
        
        int currTime = 0;
        int i = 0;
        while (true) {
            currTime = times[i][0];
            while (!occupiedQueue.isEmpty() && currTime >= occupiedQueue.peek()[0]) {
                chairQueue.add(occupiedQueue.poll()[1]);
            }

            if (currTime == targetArrivalTime) {
                return chairQueue.peek();
            }

            occupiedQueue.add(new int[]{ times[i][1], chairQueue.poll() });
            i++;
        }
    }
}
```
- Runtime: 46 ms (Beats: 75.56%)
- Memory: 48.45 MB (Beats: 87.27%)

<br>
