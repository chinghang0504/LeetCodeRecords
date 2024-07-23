# [LeetCode Records](../../README.md) - Question 2149 Rearrange Array Elements by Sign

### Attempt 1: Use two int[] to save the odd and even numbers
```java
class Solution {
    public int[] rearrangeArray(int[] nums) {
        int n = nums.length / 2;
        int[] oddNums = new int[n];
        int[] evenNums = new int[n];
        int oddSize = 0;
        int evenSize = 0;

        for (int num : nums) {
            if (num > 0) {
                oddNums[oddSize] = num;
                oddSize++;
            } else {
                evenNums[evenSize] = num;
                evenSize++;
            }
        }

        int[] answer = new int[nums.length];
        for (int i = 0; i < n; i++) {
            answer[i * 2] = oddNums[i];
            answer[i * 2 + 1] = evenNums[i];
        }

        return answer;
    }
}
```
- Runtime: 4 ms (Beats: 53.09%)
- Memory: 86.02 MB (Beats: 5.55%)

<br>
