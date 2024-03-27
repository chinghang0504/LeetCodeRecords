# [LeetCode Records](../README.md) - Question 118 Pascal's Triangle

### Attempt 1: Use an ArrayList
```java
class Solution {
    public List<List<Integer>> generate(int numRows) {
        List<List<Integer>> result = new ArrayList<>();

        result.add(Arrays.asList(1));
        if (numRows == 1) {
            return result;
        }

        result.add(Arrays.asList(1, 1));
        if (numRows == 2) {
            return result;
        }

        for (int row = 3; row <= numRows; row++) {
            List<Integer> list = new ArrayList<>();

            list.add(1);
            for (int i = 0; i < row - 2; i++) {
                List<Integer> prevList = result.get(row - 2);
                list.add(prevList.get(i) + prevList.get(i + 1));
            }
            list.add(1);

            result.add(list);
        }

        return result;
    }
}
```
- Runtime: 1 ms (Beats: 85.81%)
- Memory: 41.20 MB (Beats: 99.63%)

<br>
