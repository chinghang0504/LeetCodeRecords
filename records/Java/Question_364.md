# [LeetCode Records](../../README.md) - Question 364 Nested List Weight Sum II

### Attempt 1: Use an ArrayList to record the values and their depth
```java
class Solution {

    private static class Item {
        private int val;
        private int depth;

        Item(int val, int depth) {
            this.val = val;
            this.depth = depth;
        }
    }

    private List<Item> list;
    private int maxDepth;

    public int depthSumInverse(List<NestedInteger> nestedList) {
        list = new ArrayList<>();
        maxDepth = 0;

        depthSumInverseRecursion(nestedList, 1);

        int sum = 0;
        for (Item item : list) {
            sum += item.val * (maxDepth - item.depth + 1);
        }

        return sum;
    }

    private void depthSumInverseRecursion(List<NestedInteger> nestedList, int depth) {
        if (nestedList.isEmpty()) {
            return;
        }
        
        maxDepth = Math.max(maxDepth, depth);

        for (NestedInteger next : nestedList) {
            if (next.isInteger()) {
                list.add(new Item(next.getInteger(), depth));
            } else {
                depthSumInverseRecursion(next.getList(), depth + 1);
            }
        }
    }
}
```
- Runtime: 1 ms (Beats: 51.43%)
- Memory: 41.59 MB (Beats: 6.10%)

<br>
