# [LeetCode Records](../../README.md) - Question 2248 Intersection of Multiple Arrays

### Attempt 1: Use two boolean[] to compare the numbers
```java
class Solution {
    public List<Integer> intersection(int[][] nums) {
        boolean[] saved = new boolean[1001];

        for (int num : nums[0]) {
            saved[num] = true;
        }

        for (int i = 1; i < nums.length; i++) {
            boolean[] arr = new boolean[1001];
            for (int num : nums[i]) {
                arr[num] = true;
            }

            for (int j = 1; j < 1001; j++) {
                saved[j] = saved[j] && arr[j];
            }
        }

        List<Integer> answer = new ArrayList<>();
        for (int i = 1; i < 1001; i++) {
            if (saved[i]) {
                answer.add(i);
            }
        }

        return answer;
    }
}
```
- Runtime: 4 ms (Beats: 60.74%)
- Memory: 44.86 MB (Beats: 20.37%)

<br>
