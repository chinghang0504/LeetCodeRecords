# [LeetCode Records](../../README.md) - Question 2099 Find Subsequence of Length K With the Largest Sum

### Attempt 1: Use an int[][] to save the number and its index
```java
class Solution {
    public int[] maxSubsequence(int[] nums, int k) {
        int[][] maxNums = new int[k][2];

        for (int i = 0; i < k; i++) {
            maxNums[i][0] = Integer.MIN_VALUE;
        }

        for (int i = 0; i < nums.length; i++) {
            for (int j = 0; j < k; j++) {
                if (nums[i] >= maxNums[j][0]) {
                    swapAllRight(maxNums, j);
                    maxNums[j][0] = nums[i];
                    maxNums[j][1] = i;
                    break;
                }
            }
        }

        Arrays.sort(maxNums, (int[] o1, int[] o2) -> o1[1] - o2[1]);

        int[] answer = new int[k];
        for (int i = 0; i < k; i++) {
            answer[i] = maxNums[i][0];
        }

        return answer;
    }

    private void swapAllRight(int[][] maxNums, int start) {
        for (int i = maxNums.length - 1; i > start; i--) {
            maxNums[i][0] = maxNums[i - 1][0];
            maxNums[i][1] = maxNums[i - 1][1];
        }
    }
}
```
- Runtime: 13 ms (Beats: 10.20%)
- Memory: 44.55 MB (Beats: 36.68%)

<br>
