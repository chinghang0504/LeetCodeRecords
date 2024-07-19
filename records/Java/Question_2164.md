# [LeetCode Records](../../README.md) - Question 2164 Sort Even and Odd Indices Independently

### Attempt 1: Use Arrays.sort() twice
```java
class Solution {
    public int[] sortEvenOdd(int[] nums) {
        int n = nums.length / 2;
        int[] evenArr = new int[n + nums.length % 2];
        int[] oddArr = new int[n];

        for (int i = 0; i < n; i++) {
            evenArr[i] = nums[i * 2];
        }
        for (int i = 0; i < n; i++) {
            oddArr[i] = nums[i * 2 + 1];
        }
        if (nums.length % 2 == 1) {
            evenArr[n] = nums[nums.length - 1];
        }

        Arrays.sort(evenArr);
        Arrays.sort(oddArr);

        int[] answer = new int[nums.length];
        for (int i = 0; i < evenArr.length; i++) {
            answer[i * 2] = evenArr[i];
        }
        for (int i = 0, j = oddArr.length - 1; i < oddArr.length; i++, j--) {
            answer[i * 2 + 1] = oddArr[j];
        }

        return answer;
    }
}
```
- Runtime: 2 ms (Beats: 93.62%)
- Memory: 44.62 MB (Beats: 19.86%)

<br>
