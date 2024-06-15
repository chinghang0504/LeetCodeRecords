# [LeetCode Records](../../README.md) - Question 2073 Time Needed to Buy Tickets

### Attempt 1: Use a nested loop
```java
class Solution {
    public int timeRequiredToBuy(int[] tickets, int k) {
        int count = 0;

        while (true) {
            for (int i = 0; i < tickets.length; i++) {
                if (tickets[i] > 0) {
                    tickets[i]--;
                    count++;

                    if (tickets[k] == 0) {
                        return count;
                    }
                }
            }
        }
    }
}
```
- Runtime: 2 ms (Beats: 50.66%)
- Memory: 41.12 MB (Beats: 47.69%)

<br>

### Attempt 2: Use two loops
```java
class Solution {
    public int timeRequiredToBuy(int[] tickets, int k) {
        int count = 0;
        int val = tickets[k] - 1;

        for (int i = 0; i < tickets.length; i++) {
            count += tickets[i] < val ? tickets[i] : val;
        }

        for (int i = 0; i <= k; i++) {
            if (tickets[i] >= tickets[k]) {
                count++;
            }
        }

        return count;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 41.45 MB (Beats: 25.26%)

<br>
