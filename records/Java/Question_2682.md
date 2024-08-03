# [LeetCode Records](../../README.md) - Question 2682 Find the Losers of the Circular Game

### Attempt 1: Use a HashSet to record the player who got the ball
```java
class Solution {
    public int[] circularGameLosers(int n, int k) {
        Set<Integer> set = new HashSet<>();

        int position = 1;
        set.add(position);

        int i = 1;
        while (i < n) {
            position = getPosition(n, position, i * k);
            if (set.contains(position)) {
                break;
            } else {
                set.add(position);
                i++; 
            }
        }
        
        int[] answer = new int[n - set.size()];
        int size = 0;
        for (int j = 1; j <= n; j++) {
            if (!set.contains(j)) {
                answer[size] = j;
                size++;
            }
        }

        return answer;
    }

    private int getPosition(int n, int start, int step) {
        int val = (start + step) % n;
        return val == 0 ? n : val;
    }
}
```
- Runtime: 3 ms (Beats: 58.21%)
- Memory: 44.40 MB (Beats: 83.58%)

<br>
