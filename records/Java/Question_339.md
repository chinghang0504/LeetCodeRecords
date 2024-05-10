# [LeetCode Records](../../README.md) - Question 339 Nested List Weight Sum

### Attempt 1: Use the recursion
```java
class Solution {
    private int sum;

    public int depthSum(List<NestedInteger> nestedList) {
        sum = 0;

        depthSumRecursion(nestedList, 1);

        return sum;
    }

    private void depthSumRecursion(List<NestedInteger> nestedList, int depth) {
        for (NestedInteger item : nestedList) {
            if (item.isInteger()) {
                sum += item.getInteger() * depth;
            } else {
                depthSumRecursion(item.getList(), depth + 1);
            }
        }
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 41.33 MB (Beats: 13.68%)

<br>
