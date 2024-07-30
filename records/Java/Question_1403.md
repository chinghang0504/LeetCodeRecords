# [LeetCode Records](../../README.md) - Question 1403 Minimum Subsequence in Non-Increasing Order

### Attempt 1: Sort the array first
```java
class Solution {
    public List<Integer> minSubsequence(int[] nums) {
        Arrays.sort(nums);

        int sum = 0;
        for (int i = 0; i < nums.length; i++) {
            sum += nums[i];
        }

        int endIndex = 0;
        int localSum = 0;
        for (int i = nums.length - 1; i >= 0; i--) {
            localSum += nums[i];
            sum -= nums[i];

            if (localSum > sum) {
                endIndex = i;
                break;
            }
        }

        List<Integer> answer = new ArrayList<>();
        for (int i = nums.length - 1; i >= endIndex; i--) {
            answer.add(nums[i]);
        }

        return answer;
    }
}
```
- Runtime: 4 ms (Beats: 94.96%)
- Memory: 44.42 MB (Beats: 74.56%)

<br>
