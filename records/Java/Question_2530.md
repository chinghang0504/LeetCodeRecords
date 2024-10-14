# [LeetCode Records](../../README.md) - Question 2530 Maximal Score After Applying K Operations

### Attempt 1: Use a Priority Queue to store the numbers
```java
class Solution {
    public long maxKelements(int[] nums, int k) {
        Arrays.sort(nums);

        PriorityQueue<Integer> priorityQueue = new PriorityQueue<>((a, b) -> b - a);
        for (int i = Math.max(0, nums.length - k); i < nums.length; i++) {
            priorityQueue.add(nums[i]);
        }

        long sum = 0;
        for (int i = 0; i < k; i++) {
            int val = priorityQueue.poll();
            sum += val;
            priorityQueue.add(Math.ceilDiv(val, 3));
        }

        return sum;
    }
}
```
- Runtime: 111 ms (Beats: 100.00%)
- Memory: 62.00 MB (Beats: 93.84%)

<br>
