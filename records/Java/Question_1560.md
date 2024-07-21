# [LeetCode Records](../../README.md) - Question 1560 Most Visited Sector in a Circular Track

### Attempt 1: Use a nested loop to record the counts
```java
class Solution {
    public List<Integer> mostVisited(int n, int[] rounds) {
        int[] counts = new int[n + 1];

        counts[rounds[0]]++;
        for (int i = 0; i < rounds.length - 1; i++) {
            int start = rounds[i];
            int end = rounds[i + 1];
            int curr = start;
            while (curr != end) {
                curr = curr == n ? 0 : curr + 1;
                counts[curr]++;
            }
        }

        int max = Integer.MIN_VALUE;
        List<Integer> answer = null;
        for (int i = 1; i <= n; i++) {
            if (counts[i] > max) {
                max = counts[i];
                answer = new ArrayList<>();
                answer.add(i);
            } else if (counts[i] == max) {
                answer.add(i);
            }
        }

        return answer;
    }
}
```
- Runtime: 2 ms (Beats: 41.30%)
- Memory: 43.03 MB (Beats: 28.99%)

<br>
