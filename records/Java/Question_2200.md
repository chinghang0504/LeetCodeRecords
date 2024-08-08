# [LeetCode Records](../../README.md) - Question 2200 Find All K-Distant Indices in an Array

### Attempt 1: Use a boolean[] to save the indices
```java
class Solution {
    public List<Integer> findKDistantIndices(int[] nums, int key, int k) {
        boolean[] saved = new boolean[nums.length];

        for (int i = 0; i < nums.length; i++) {
            if (nums[i] == key) {
                int start = Math.max(0, i - k);
                for (int j = start; j < i; j++) {
                    saved[j] = true;
                }

                saved[i] = true;

                int end = Math.min(nums.length - 1, i + k);
                for (int j = i + 1; j <= end; j++) {
                    saved[j] = true;
                }
            }
        }

        List<Integer> answer = new ArrayList<>();
        for (int i = 0; i < saved.length; i++) {
            if (saved[i]) {
                answer.add(i);
            }
        }

        return answer;
    }
}
```
- Runtime: 5 ms (Beats: 67.95%)
- Memory: 44.30 MB (Beats: 90.21%)

<br>
