# [LeetCode Records](../../README.md) - Question 769 Max Chunks To Make Sorted

### Attempt 1: Use a PriorityQueue to store the numbers that are larger than the current index
```java
class Solution {
    public int maxChunksToSorted(int[] arr) {
        Queue<Integer> priorityQueue = new PriorityQueue<>();
        int count = 0;
        int currSize = 0;
        int nextStart = 0;
        for (int i = 0; i < arr.length; i++) {
            if (arr[i] <= i) {
                currSize++;
                while (!priorityQueue.isEmpty() && priorityQueue.peek() <= i) {
                    priorityQueue.poll();
                    currSize++;
                }

                if (nextStart + currSize - 1 == i) {
                    count++;
                    currSize = 0;
                    nextStart = i + 1;
                }
            } else {
                priorityQueue.add(arr[i]);
            }
        }

        return count;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 40.82 MB (Beats: 62.65%)

<br>
