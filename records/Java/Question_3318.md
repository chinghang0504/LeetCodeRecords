# [LeetCode Records](../../README.md) - Question 3318 Find X-Sum of All K-Long Subarrays I

### Attempt 1: Use a HashMap to store the number and its count key-value pairs
```java
class Solution {

    private int x;
    private Map<Integer, Integer> map;

    public int[] findXSum(int[] nums, int k, int x) {
        this.x = x;
        this.map = new HashMap<>();
        int size = nums.length - k + 1;
        int[] ans = new int[size];

        for (int i = 0; i < k; i++) {
            map.merge(nums[i], 1, Integer::sum);
        }
        ans[0] = getLocalSum();

        for (int i = 1; i < size; i++) {
            int target1 = nums[i - 1];
            Integer count1 = map.get(target1);
            if (count1 == 1) {
                map.remove(target1);
            } else {
                map.put(target1, count1 - 1);
            }

            int target2 = nums[i + k - 1];
            Integer count2 = map.get(target2);
            if (count2 == null) {
                map.put(target2, 1);
            } else {
                map.put(target2, count2 + 1);
            }

            ans[i] = getLocalSum();
        }

        return ans;
    }

    private int getLocalSum() {
        List<Map.Entry<Integer, Integer>> list = new ArrayList<>(map.entrySet());
        list.sort((e1, e2) -> {
            int count1 = e1.getValue();
            int count2 = e2.getValue();
            return count1 != count2 ? count2 - count1 : e2.getKey() - e1.getKey();
        });

        int listSize = Math.min(x, list.size());
        int localSum = 0;
        for (int j = 0; j < listSize; j++) {
            Map.Entry<Integer, Integer> entry = list.get(j);
            localSum += entry.getKey() * entry.getValue();
        }

        return localSum;
    }
}
```
- Runtime: 11 ms (Beats: 100.00%)
- Memory: 44.85 MB (Beats: 100.00%)

<br>
