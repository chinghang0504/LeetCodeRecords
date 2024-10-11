# [LeetCode Records](../../README.md) - Question 1090 Largest Values From Labels

### Attempt 1: Use an int[][] to store the value and the label key-value pairs and a HashMap to store the label and the count key-value pairs
```java
class Solution {
    public int largestValsFromLabels(int[] values, int[] labels, int numWanted, int useLimit) {
        int n = values.length;
        int[][] nums = new int[n][2];
        for (int i = 0; i < n; i++) {
            nums[i][0] = values[i];
            nums[i][1] = labels[i];
        }

        Arrays.sort(nums, (num1, num2) -> num2[0] - num1[0]);

        Map<Integer, Integer> map = new HashMap<>();
        int sum = 0;
        int numCount = 0;
        for (int i = 0; i < n && numCount < numWanted; i++) {
            int val = nums[i][0];
            int label = nums[i][1];

            Integer count = map.get(label);
            if (count == null) {
                map.put(label, 1);
                sum += val;
                numCount++;
            } else if (count < useLimit) {
                map.put(label, count + 1);
                sum += val;
                numCount++;
            }
        }

        return sum;
    }
}
```
- Runtime: 16 ms (Beats: 92.17%)
- Memory: 46.00 MB (Beats: 74.65%)

<br>
