# [LeetCode Records](../README.md) - Question 260 Single Number III

### Attempt 1: Use a HashMap
```java
class Solution {
    
    private static final int[] result = new int[2];
    private int count;

    public int[] singleNumber(int[] nums) {
        Map<Integer, Integer> map = new HashMap<>();
        for (int i = 0; i < nums.length; i++) {
            map.merge(nums[i], 1, Integer::sum);
        }

        map.entrySet().stream()
            .filter(a -> a.getValue() == 1)
            .forEach(a -> {
                result[count++] = a.getKey();
        });

        return result;
    }
}
```
- Runtime: 7 ms (Beats: 19.39%)
- Memory: 45.88 MB (Beats: 14.00%)

<br>
