# [LeetCode Records](../../README.md) - Question 1441 Build an Array With Stack Operations

### Attempt 1: Use a variable to reocrd the current target index and a variable to record the current number
```java
class Solution {
    public List<String> buildArray(int[] target, int n) {
        List<String> ans = new ArrayList<>();
        int currNum = 1;
        int currTargetIndex = 0;

        while (currTargetIndex < target.length) {
            ans.add("Push");

            if (target[currTargetIndex] != currNum) {
                ans.add("Pop");
            } else {
                currTargetIndex++;
            }
            
            currNum++;
        }

        return ans;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 42.37 MB (Beats: 96.01%)

<br>
