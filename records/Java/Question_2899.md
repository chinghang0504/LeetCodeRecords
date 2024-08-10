# [LeetCode Records](../../README.md) - Question 2899 Last Visited Integers

### Attempt 1: Use two List to record the numbers
```java
class Solution {
    public List<Integer> lastVisitedIntegers(int[] nums) {
        List<Integer> seen = new LinkedList<>();
        List<Integer> ans = new ArrayList<>();
        int k = 1;
        boolean prevMinusOne = false;

        for (int num : nums) {
            if (num != -1) {
                seen.addFirst(num);
                prevMinusOne = false;
            } else {
                if (!prevMinusOne) {
                    k = 1;
                }

                if (k <= seen.size()) {
                    ans.addLast(seen.get(k - 1));
                    k++;
                } else {
                    ans.addLast(-1);
                }
                
                prevMinusOne = true;
            }
        }
        
        return ans;
    }
}
```
- Runtime: 2 ms (Beats: 40.47%)
- Memory: 44.63 MB (Beats: 22.79%)

<br>
