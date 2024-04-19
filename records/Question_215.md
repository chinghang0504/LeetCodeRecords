# [LeetCode Records](../README.md) - Question 215 Kth Largest Element in an Array

### Attempt 1: Use a PriorityQueue
```java
class Solution {
    public int findKthLargest(int[] nums, int k) {
        PriorityQueue<Integer> priorityQueue = new PriorityQueue<>(new Comparator<Integer>() {
            @Override
            public int compare(Integer o1, Integer o2) {
                return o1.compareTo(o2) * -1;
            }
        });

        for (int i = 0; i < nums.length; i++) {
            priorityQueue.add(nums[i]);
        }

        for (int i = 0; i < k - 1; i++) {
            priorityQueue.poll();
        }

        return priorityQueue.poll();
    }
}
```
- Runtime: 66 ms (Beats: 23.61%)
- Memory: 58.33 MB (Beats: 37.43%)

<br>

### Attempt 2: Use an int array to record numbers
```java
class Solution {
    public int findKthLargest(int[] nums, int k) {
        int[] saved = new int[20001];
        for (int num: nums) {
            saved[num + 10000]++;
        }

        for (int i = 20000; i >= 0; i--) {
            k -= saved[i];

            if (k <= 0) {
                return i - 10000;
            }
        }

        return -1;
    }
}
```
- Runtime: 2 ms (Beats: 100.00%)
- Memory: 55.40 MB (Beats: 98.18%)

<br>
