# [LeetCode Records](../README.md) - Question 119 Pascal's Triangle II

### Attempt 1: Use an ArrayList
```java
class Solution {
    public List<Integer> getRow(int rowIndex) {
        List<List<Integer>> result = new ArrayList<>();

        result.add(Arrays.asList(1));
        if (rowIndex == 0) {
            return result.get(0);
        }

        result.add(Arrays.asList(1, 1));
        if (rowIndex == 1) {
            return result.get(1);
        }

        for (int row = 2; row <= rowIndex; row++) {
            List<Integer> list = new ArrayList<>();

            list.add(1);
            for (int i = 0; i < row - 1; i++) {
                List<Integer> prevList = result.get(row - 1);
                list.add(prevList.get(i) + prevList.get(i + 1));
            }
            list.add(1);

            result.add(list);
        }

        return result.get(rowIndex);
    }
}
```
- Runtime: 2 ms (Beats: 16.12%)
- Memory: 40.52 MB (Beats: 96.87%)

<br>

### Attempt 2: Only record the previous list
```java
class Solution {
    public List<Integer> getRow(int rowIndex) {
        if (rowIndex == 0) {
            return Arrays.asList(1);
        }

        List<Integer> prevList = Arrays.asList(1, 1);
        if (rowIndex == 1) {
            return prevList;
        }

        for (int row = 2; row <= rowIndex; row++) {
            List<Integer> list = new ArrayList<>();

            list.add(1);
            for (int i = 0; i < row - 1; i++) {
                list.add(prevList.get(i) + prevList.get(i + 1));
            }
            list.add(1);

            prevList = list;
        }

        return prevList;
    }
}
```
- Runtime: 1 ms (Beats: 75.08%)
- Memory: 41.01 MB (Beats: 48.95%)

<br>
