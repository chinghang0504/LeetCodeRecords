# [LeetCode Records](../README.md) - Question 347 Top K Frequent Elements

### Attempt 1: Use HashMap to record the frequency and sort the map
```java
class Solution {
    public int[] topKFrequent(int[] nums, int k) {
        Map<Integer, Integer> map = new HashMap<>();
        for (int i = 0; i < nums.length; i++) {
            map.merge(nums[i], 1, Integer::sum);
        }

        int[] result = new int[k];
        int size = 0;
        Iterator<Map.Entry<Integer, Integer>> iterator = map.entrySet().stream().sorted((a, b) -> {
            int val1 = a.getValue();
            int val2 = b.getValue();
            if (val1 > val2) {
                return -1;
            } else if (val1 < val2) {
                return 1;
            } else {
                return 0;
            }
        }).iterator();
        
        for (int i = 0; i < k; i++) {
            result[size++] = iterator.next().getKey();
        }
        
        return result;
    }
}
```
- Runtime: 15 ms (Beats: 47.86%)
- Memory: 48.64 MB (Beats: 35.12%)

<br>
