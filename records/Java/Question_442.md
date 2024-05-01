# [LeetCode Records](../../README.md) - Question 442 Find All Duplicates in an Array

### Attempt 1: Use a HashMap
```java
class Solution {
    public List<Integer> findDuplicates(int[] nums) {
        Map<Integer, Integer> map = new HashMap<>(nums.length);
        for (int i : nums) {
            map.merge(i, 1, Integer::sum);
        }

        return map.entrySet().stream()
                .filter(x -> x.getValue() == 2)
                .map(Map.Entry::getKey)
                .toList();
    }
}
```
- Runtime: 22 ms (Beats: 12.91%)
- Memory: 55.35 MB (Beats: 8.79%)

<br>
