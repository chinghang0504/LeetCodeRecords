# [LeetCode Records](../../README.md) - Question 1409 Queries on a Permutation With Key

### Attempt 1: Use an ArrayList to store the numbers
```java
class Solution {
    public int[] processQueries(int[] queries, int m) {
        int[] ans = new int[queries.length];
        List<Integer> list = new ArrayList<>();
        for (int i = 1; i <= m; i++) {
            list.add(i);
        }

        for (int i = 0; i < queries.length; i++) {
            int index = list.indexOf((Integer)queries[i]);
            ans[i] = index;
            list.remove(index);
            list.addFirst(queries[i]);
        }

        return ans;
    }
}
```
- Runtime: 8 ms (Beats: 56.54%)
- Memory: 42.52 MB (Beats: 55.50%)

<br>
