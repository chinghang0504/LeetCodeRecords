# [LeetCode Records](../../README.md) - Question 2869 Minimum Operations to Collect Elements

### Attempt 1: Use a boolean[] to record if the number is checked
```java
class Solution {
    public int minOperations(List<Integer> nums, int k) {
        int[] arr = new int[nums.size()];
        int size = 0;
        for (int num : nums) {
            arr[size] = num;
            size++;
        }

        boolean[] checked = new boolean[k];
        int count = 0;
        for (int i = arr.length - 1; i >= 0; i--) {
            int val = arr[i];
            if (val >= 1 && val <= k && !checked[val - 1]) {
                checked[val - 1] = true;
                count++;

                if (count == k) {
                    return arr.length - i;
                }
            }
        }

        return -1;
    }
}
```
- Runtime: 1 ms (Beats: 99.37%)
- Memory: 41.67 MB (Beats: 89.87%)

<br>
