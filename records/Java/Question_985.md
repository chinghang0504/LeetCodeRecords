# [LeetCode Records](../../README.md) - Question 985 Sum of Even Numbers After Queries

### Attempt 1: Track the sum of even numbers
```java
class Solution {
    public int[] sumEvenAfterQueries(int[] nums, int[][] queries) {
        int sumOfEven = 0;
        for (int num : nums) {
            if (num % 2 == 0) {
                sumOfEven += num;
            }
        }

        int[] ans = new int[queries.length];
        for (int i = 0; i < queries.length; i++) {
            int index = queries[i][1];
            int val = queries[i][0];
            int nextVal = nums[index] + val;
            
            if (nums[index] % 2 == 0) {
                if (nextVal % 2 == 0) {
                    sumOfEven = sumOfEven - nums[index] + nextVal;
                } else {
                    sumOfEven -= nums[index];
                }
            } else if (nextVal % 2 == 0) {
                sumOfEven += nextVal;
            }

            nums[index] = nextVal;
            ans[i] = sumOfEven;
        }

        return ans;
    }
}
```
- Runtime: 4 ms (Beats: 99.16%)
- Memory: 49.23 MB (Beats: 24.51%)

<br>
