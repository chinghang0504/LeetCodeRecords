# [LeetCode Records](../../README.md) - Question 487 Max Consecutive Ones II

### Attempt 1: Use an ArrayList to store the item with the start index and its number of consecutive 1's
```java
class Solution {
    public int findMaxConsecutiveOnes(int[] nums) {
        List<int[]> list = new ArrayList<>();

        int startIndex = 0;
        int oneCount = 0;
        for (int i = 0; i < nums.length; i++) {
            if (nums[i] == 1) {
                if (oneCount == 0) {
                    startIndex = i;
                }
                oneCount++;
            } else if (oneCount > 0) {
                list.add(new int[]{ startIndex, oneCount });
                oneCount = 0;
            }
        }
        if (oneCount > 0) {
            list.add(new int[]{ startIndex, oneCount });
        }

        int size = list.size();
        if (size == 0) {
            return 1;
        } else if (size == 1) {
            int count = list.get(0)[1];
            return count == nums.length ? count : count + 1;
        }

        int maxCount = list.get(0)[1] + 1;
        for (int i = 1; i < size; i++) {
            int[] first = list.get(i - 1);
            int[] second = list.get(i);
            if (first[0] + first[1] + 1 == second[0]) {
                maxCount = Math.max(maxCount, first[1] + second[1] + 1);
            } else {
                maxCount = Math.max(maxCount, second[1] + 1);
            }
        }

        return maxCount;
    }
}
```
- Runtime: 2 ms (Beats: 98.18%)
- Memory: 45.58 MB (Beats: 57.23%)

<br>
