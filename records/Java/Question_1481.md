# [LeetCode Records](../../README.md) - Question 1481 Least Number of Unique Integers after K Removals

### Attempt 1: Use a HashMap to store the number and count key-value pairs
```java
class Solution {
    public int findLeastNumOfUniqueInts(int[] arr, int k) {
        Map<Integer, Integer> map = new HashMap<>();
        for (int num : arr) {
            map.merge(num, 1, Integer::sum);
        }

        List<Integer> counts = new ArrayList<>(map.values());
        counts.sort(null);

        int removedCount = 0;
        for (int count : counts) {
            if (count <= k) {
                removedCount++;
                k -= count;
            } else {
                break;
            }
        }

        return counts.size() - removedCount;
    }
}
```
- Runtime: 36 ms (Beats: 94.54%)
- Memory: 57.02 MB (Beats: 66.51%)

<br>
