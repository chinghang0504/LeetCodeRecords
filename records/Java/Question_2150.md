# [LeetCode Records](../../README.md) - Question 2150 Find All Lonely Numbers in the Array

### Attempt 1: Use a HashMap to store the number and its count key-value pairs
```java
class Solution {
    public List<Integer> findLonely(int[] nums) {
        Map<Integer, Integer> map = new HashMap<>();
        for (int num : nums) {
            map.merge(num, 1, Integer::sum);
        }

        List<Integer> ans = new ArrayList<>();
        for (int num : nums) {
            if (map.get(num) == 1 && map.get(num - 1) == null && map.get(num + 1) == null) {
                ans.add(num);
            }
        }

        return ans;
    }
}
```
- Runtime: 76 ms (Beats: 44.86%)
- Memory: 64.26 MB (Beats: 75.14%)

<br>
