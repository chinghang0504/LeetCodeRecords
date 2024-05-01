# [LeetCode Records](../../README.md) - Question 682 Baseball Game

### Attempt 1: Use an int array to save scores
```java
class Solution {
    private final int[] scores = new int[1000];
    
    public int calPoints(String[] operations) {
        int curr = 0;

        for (String operation : operations) {
            switch (operation) {
                case "+" -> {
                    scores[curr] = scores[curr - 1] + scores[curr - 2];
                    curr++;
                }
                case "D" -> {
                    scores[curr] = scores[curr - 1] * 2;
                    curr++;
                }
                case "C" -> {
                    curr--;
                }
                default -> {
                    scores[curr] = Integer.parseInt(operation);
                    curr++;
                }
            }
        }

        int sum = 0;
        for (int i = 0; i < curr; i++) {
            sum += scores[i];
        }
        return sum;
    }
}
```
- Runtime: 1 ms (Beats: 100.00%)
- Memory: 41.66 MB (Beats: 50.63%)

<br>
