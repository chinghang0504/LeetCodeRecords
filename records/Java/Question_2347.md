# [LeetCode Records](../../README.md) - Question 2347 Best Poker Hand

### Attempt 1: Use two helper functions
```java
class Solution {
    public String bestHand(int[] ranks, char[] suits) {
        if (isFlush(suits)) {
            return "Flush";
        }

        int rank = checkRank(ranks);
        if (rank == 2) {
            return "Three of a Kind";
        } else if (rank == 1) {
            return "Pair";
        } else {
            return "High Card";
        }
    }

    private boolean isFlush(char[] suits) {
        char suit = suits[0];

        for (int i = 1; i < suits.length; i++) {
            if (suits[i] != suit) {
                return false;
            }
        }

        return true;
    }

    private int checkRank(int[] ranks) {
        int[] counts = new int[14];

        for (int rank : ranks) {
            counts[rank]++;
        }

        for (int i = 1; i < 14; i++) {
            if (counts[i] >= 3) {
                return 2;
            }
        }

        for (int i = 1; i < 14; i++) {
            if (counts[i] == 2) {
                return 1;
            }
        }

        return 0;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 40.92 MB (Beats: 64.02%)

<br>
