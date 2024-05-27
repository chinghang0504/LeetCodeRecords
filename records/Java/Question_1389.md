# [LeetCode Records](../../README.md) - Question 1389 Create Target Array in the Given Order

### Attempt 1: Use a LinkedList
```java
class Solution {
    public int[] createTargetArray(int[] nums, int[] index) {
        List<Integer> list = new LinkedList<>();

        for (int i = 0; i < nums.length; i++) {
            list.add(index[i], nums[i]);
        }

        int[] target = new int[nums.length];
        int i = 0;
        for (int num : list) {
            target[i] = num;
            i++;
        }

        return target;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 41.77 MB (Beats: 40.30%)

<br>
