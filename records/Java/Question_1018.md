# [LeetCode Records](../../README.md) - Question 1018 Binary Prefix Divisible By 5

### Attempt 1: Check the last digit
```java
class Solution {
    public List<Boolean> prefixesDivBy5(int[] nums) {
        List<Boolean> answer = new ArrayList<>();

        int val = 0;
        for (int num : nums) {
            val = ((val << 1) | num) % 10;
            answer.add(val % 5 == 0);
        }

        return answer;
    }
}
```
- Runtime: 3 ms (Beats: 99.65%)
- Memory: 45.09 MB (Beats: 97.57%)

<br>
