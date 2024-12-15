# [LeetCode Records](../../README.md) - Question 2343 Query Kth Smallest Trimmed Number

### Attempt 1: Create a class that can store the index and its num
```java
class Solution {

    class Item {
        
        int index;
        String num;
    }

    public int[] smallestTrimmedNumbers(String[] nums, int[][] queries) {
        int len = nums[0].length();
        int[] ans = new int[queries.length];
        Item[] items = new Item[nums.length];
        for (int i = 0; i < nums.length; i++) {
            items[i] = new Item();
        }

        for (int i = 0; i < queries.length; i++) {
            int k = queries[i][0];
            int currLen = queries[i][1];

            for (int j = 0; j < nums.length; j++) {
                items[j].index = j;
                items[j].num = nums[j].substring(len - currLen);
            }

            Arrays.sort(items, (item1, item2) -> {
                return item1.num.compareTo(item2.num);
            });

            ans[i] = items[k - 1].index;
        }

        return ans;
    }
}
```
- Runtime: 209 ms (Beats: 63.77%)
- Memory: 45.83 MB (Beats: 24.66%)

<br>
