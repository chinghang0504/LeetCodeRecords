# [LeetCode Records](../../README.md) - Question 1823 Find the Winner of the Circular Game

### Attempt 1: Use a LinkedList to simulate the case
```java
class Solution {
    public int findTheWinner(int n, int k) {
        List<Integer> list = new LinkedList<>();
        for (int i = 1; i <= n; i++) {
            list.add(i);
        }

        while (list.size() > 1) {
            for (int i = 0; i < k - 1; i++) {
                list.addLast(list.removeFirst());
            }
            list.removeFirst();
        }

        return list.get(0);
    }
}
```
- Runtime: 44 ms (Beats: 11.38%)
- Memory: 44.46 MB (Beats: 8.34%)

<br>
