# [LeetCode Records](../../README.md) - Question 3371 Identify the Largest Outlier in an Array

### Attempt 1: Use a HashMap to store the number and its count
```java
class Solution {
    public int getLargestOutlier(int[] nums) {
        int sum = 0;
        Map<Integer, Integer> map = new HashMap<>();
        for (int num : nums) {
            sum += num;
            map.merge(num, 1, Integer::sum);
        }

        int maxOutlier = Integer.MIN_VALUE;
        for (int i = 0; i < nums.length; i++) {
            int remainder = sum - nums[i];
            if (remainder % 2 == 0) {
                int target = remainder / 2;
                if (nums[i] != target) {
                    Integer count = map.get(target);
                    if (count != null && count > 0) {
                        maxOutlier = Math.max(maxOutlier, nums[i]);
                    }
                } else {
                    Integer count = map.get(target);
                    if (count != null && count > 1) {
                        maxOutlier = Math.max(maxOutlier, nums[i]);
                    }
                }
            }
        }

        return maxOutlier;
    }
}
```
- Runtime: 76 ms (Beats: 89.60%)
- Memory: 60.75 MB (Beats: 26.03%)

<br>
