# [LeetCode Records](../../README.md) - Question 1852 Distinct Numbers in Each Subarray

### Attempt 1: Use a HashMap to store the integer counts
```java
class Solution {
    public int[] distinctNumbers(int[] nums, int k) {
        Map<Integer, Integer> map = new HashMap<>();
        for (int i = 0; i < k; i++) {
            map.merge(nums[i], 1, Integer::sum);
        }

        int size = nums.length - k + 1;
        int[] ans = new int[size];
        ans[0] = map.size();

        for (int i = 1; i < size; i++) {
            map.merge(nums[i + k - 1], 1, Integer::sum);
            
            int count = map.get(nums[i - 1]);
            if (count == 1) {
                map.remove(nums[i - 1]);
            } else {
                map.put(nums[i - 1], count - 1);
            }

            ans[i] = map.size();
        }

        return ans;
    }
}
```
- Runtime: 52 ms (Beats: 96.49%)
- Memory: 63.01 MB (Beats: 7.02%)

<br>
