# [LeetCode Records](../../README.md) - Question 2161 Partition Array According to Given Pivot

### Attempt 1: Use three loops
```java
class Solution {
    public int[] pivotArray(int[] nums, int pivot) {
        int[] answer = new int[nums.length];
        int curr = 0;
        int pivotCount = 0;

        for (int i = 0; i < nums.length; i++) {
            if (nums[i] < pivot) {
                answer[curr] = nums[i];
                curr++;
            } else if (nums[i] == pivot) {
                pivotCount++;
            }
        }

        for (int i = 0; i < pivotCount; i++) {
            answer[curr] = pivot;
            curr++;
        }

        for (int i = 0; i < nums.length; i++) {
            if (nums[i] > pivot) {
                answer[curr] = nums[i];
                curr++;
            }
        }

        return answer;
    }
}
```
- Runtime: 4 ms (Beats: 100.00%)
- Memory: 68.32 MB (Beats: 7.68%)

<br>
