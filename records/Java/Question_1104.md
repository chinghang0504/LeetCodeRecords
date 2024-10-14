# [LeetCode Records](../../README.md) - Question 1104 Path In Zigzag Labelled Binary Tree

### Attempt 1: Use an ArrayList to store the end number of each row
```java
class Solution {
    public List<Integer> pathInZigZagTree(int label) {
        List<Integer> list = new ArrayList<>();
        int i = 2;
        while (i <= label) {
            list.add(i - 1);
            i *= 2;
        }
        list.add(i - 1);

        boolean isReversed = false;
        List<Integer> ans = new ArrayList<>();
        while (label > 0) {
            int end = list.removeLast();

            if (isReversed) {
                int start = (end + 1) / 2;
                int diff = label - start;
                ans.addFirst(end - diff);
            } else {
                ans.addFirst(label);
            }
            
            label /= 2;
            isReversed = !isReversed;
        }

        return ans;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 40.74 MB (Beats: 81.25%)

<br>
