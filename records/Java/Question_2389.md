# [LeetCode Records](../../README.md) - Question 2389 Longest Subsequence With Limited Sum

### Attempt 1: Use Arrays.sort() and a helper function that tests each number
```java
class Solution {
    public int[] answerQueries(int[] nums, int[] queries) {
        int[] answer = new int[queries.length];
        
        Arrays.sort(nums);

        for (int i = 0; i < queries.length; i++) {
            answer[i] = getMaxSize(nums, queries[i]);
        }

        return answer;
    }

    private int getMaxSize(int[] nums, int query) {
        int count = 0;
        int sum = 0;

        for (int num : nums) {
            int nextSum = sum + num;
            if (nextSum <= query) {
                sum = nextSum;
                count++;
            } else {
                break;
            }
        }

        return count;
    }
}
```
- Runtime: 6 ms (Beats: 59.11%)
- Memory: 44.93 MB (Beats: 30.14%)

<br>
