# [LeetCode Records](../../README.md) - Question 1695 Maximum Erasure Value

### Attempt 1: Use a HashMap to store the number with its last index key-value pairs
```java
class Solution {
    public int maximumUniqueSubarray(int[] nums) {
        Map<Integer, Integer> lastNumMap = new HashMap<>();
        int startIndex = 0;
        int currSum = 0;
        int maxSum = 0;
        for (int i = 0; i < nums.length; i++) {
            if (!lastNumMap.containsKey(nums[i])) {
                lastNumMap.put(nums[i], i);
                currSum += nums[i];
                maxSum = Math.max(maxSum, currSum);
            } else {
                int prevIndex = lastNumMap.get(nums[i]);
                for (int j = startIndex; j < prevIndex; j++) {
                    currSum -= nums[j];
                    lastNumMap.remove(nums[j]);
                }
                startIndex = prevIndex + 1;
                lastNumMap.put(nums[i], i);
            }
        }

        return maxSum;
    }
}
```
- Runtime: 41 ms (Beats: 88.56%)
- Memory: 59.88 MB (Beats: 52.22%)

<br>
