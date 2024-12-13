# [LeetCode Records](../../README.md) - Question 2055 Plates Between Candles

### Attempt 1: Use an ArrayList to store the cumulative counts
```java
class Solution {

    class Item {
        int index;
        int count;

        Item(int index, int count) {
            this.index = index;
            this.count = count;
        }
    }
    
    public int[] platesBetweenCandles(String s, int[][] queries) {
        char[] arr = s.toCharArray();
        List<Item> list = new ArrayList<>();

        for (int i = 0, currCount = 0; i < arr.length; i++) {
            if (arr[i] == '|') {
                list.add(new Item(i, currCount));
            } else {
                currCount++;
            }
        }

        int size = list.size();
        int[] ans = new int[queries.length];
        for (int i = 0; i < queries.length; i++) {
            int start = 0;
            int startCount = 0;
            for (; start < size; start++) {
                Item item = list.get(start);
                if (item.index >= queries[i][0]) {
                    startCount = item.count;
                    break;
                }
            }

            int end = size - 1;
            int endCount = 0;
            for (; end >= 0; end--) {
                Item item = list.get(end);
                if (item.index <= queries[i][1]) {
                    endCount = item.count;
                    break;
                }
            }

            ans[i] = start >= end ? 0 : endCount - startCount;
        }

        return ans;
    }
}
```
- Runtime: 1242 ms (Beats: 5.01%)
- Memory: 79.28 MB (Beats: 79.71%)

<br>
