# [LeetCode Records](../../README.md) - Question 3159 Find Occurrences of an Element in an Array

### Attempt 1: Use an ArrayList to store the indices of x
```java
class Solution {
    public int[] occurrencesOfElement(int[] nums, int[] queries, int x) {
        List<Integer> list = new ArrayList<>();

        for (int i = 0; i < nums.length; i++) {
            if (nums[i] == x) {
                list.add(i);
            }
        }

        int size = list.size();
        int[] ans = new int[queries.length];
        for (int i = 0; i < queries.length; i++) {
            int query = queries[i];
            ans[i] = query > size ? -1 : list.get(query - 1);
        }

        return ans;
    }
}
```
- Runtime: 5 ms (Beats: 83.89%)
- Memory: 64.25 MB (Beats: 52.38%)

<br>
