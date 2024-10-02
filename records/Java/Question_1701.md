# [LeetCode Records](../../README.md) - Question 1701 Average Waiting Time

### Attempt 1: Track the current time
```java
class Solution {
    public double averageWaitingTime(int[][] customers) {
        int currTime = 0;
        double totalTime = 0;

        for (int[] customer : customers) {
            if (currTime > customer[0]) {
                totalTime += currTime - customer[0];
            } else {
                currTime = customer[0];
            }
            totalTime += customer[1];
            currTime += customer[1]; 
        }

        return totalTime / customers.length;
    }
}
```
- Runtime: 3 ms (Beats: 94.09%)
- Memory: 72.37 MB (Beats: 94.55%)

<br>
