# [LeetCode Records](../../README.md) - Question 2070 Most Beautiful Item for Each Query

### Attempt 1: Use Arrays.sort() to sort the array and create a list that stores the price and its maximum beauty
```java
class Solution {
    public int[] maximumBeauty(int[][] items, int[] queries) {
        Arrays.sort(items, (item1, item2) -> item1[0] - item2[0]);

        List<int[]> list = new ArrayList<>();
        int[] head = items[0];
        list.add(head);
        for (int i = 1; i < items.length; i++) {
            if (items[i][0] == head[0]) {
                head[1] = Math.max(head[1], items[i][1]);
            } else if (items[i][1] > head[1]) {
                head = items[i];
                list.addFirst(head);
            }
        }

        int[] ans = new int[queries.length];
        for (int i = 0; i < queries.length; i++) {
            ans[i] = 0;

            for (int[] item : list) {
                if (queries[i] >= item[0]) {
                    ans[i] = item[1];
                    break;
                }
            }
        }

        return ans;
    }
}
```
- Runtime: 30 ms (Beats: 98.63%)
- Memory: 80.83 MB (Beats: 59.15%)

<br>
