# [LeetCode Records](../../README.md) - Question 3173 Bitwise OR of Adjacent Elements

### Attempt 1: 
```java
class Solution {
    public int[] orArray(int[] nums) {
        int[] answer = new int[nums.length - 1];

        for (int i = 0; i < nums.length - 1; i++) {
            answer[i] = nums[i] | nums[i + 1];
        }

        return answer;
    }
}
```
- Runtime: 1 ms (Beats: 100.00%)
- Memory: 45.40 MB (Beats: 53.01%)

<br>
