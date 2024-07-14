# [LeetCode Records](../../README.md) - Question 2545 Sort the Students by Their Kth Score

### Attempt 1: Use Arrays.sort()
```java
class Solution {
    public int[][] sortTheStudents(int[][] score, int k) {
        Arrays.sort(score, (a ,b) -> b[k] - a[k]);
        return score;
    }
}
```
- Runtime: 2 ms (Beats: 92.73%)
- Memory: 52.12 MB (Beats: 50.63%)

<br>
