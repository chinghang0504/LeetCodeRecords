# [LeetCode Records](../../README.md) - Question 2483 Minimum Penalty for a Shop

### Attempt 1: Track the number of hours that has customers
```java
class Solution {
    public int bestClosingTime(String customers) {
        char[] arr = customers.toCharArray();
        int openCount = 0;
        for (char ch : arr) {
            if (ch == 'Y') {
                openCount++;
            }
        }
        int closeCount = 0;

        int minPenalty = openCount;
        int minPenaltyHour = 0;
        for (int i = 0; i < arr.length; i++) {
            char ch = arr[i];
            if (ch == 'Y') {
                openCount--;
            } else {
                closeCount++;
            }

            int penalty = closeCount + openCount;
            if (penalty < minPenalty) {
                minPenalty = penalty;
                minPenaltyHour = i + 1;
            }
        }

        return minPenaltyHour;
    }
}
```
- Runtime: 9 ms (Beats: 76.08%)
- Memory: 45.06 MB (Beats: 75.28%)

<br>
