# [LeetCode Records](../../README.md) - Question 1424 Diagonal Traverse II

### Attempt 1: Use a HashMap to store the sum and its list key-value pairs
```java
class Solution {
    public int[] findDiagonalOrder(List<List<Integer>> nums) {
        int size = 0;
        Map<Integer, List<Integer>> map = new HashMap<>();
        int i = 0;
        for (List<Integer> numList : nums) {
            int j = 0;
            for (int num : numList) {
                int sum = i + j;

                List<Integer> list = map.get(sum);
                if (list == null) {
                    list = new ArrayList<>();
                    map.put(sum, list);
                }
                list.addFirst(num);

                j++;
                size++;
            }
            
            i++;
        }

        List<Map.Entry<Integer, List<Integer>>> ansList = new ArrayList(map.entrySet());
        ansList.sort((entry1, entry2) -> entry1.getKey() - entry2.getKey());

        int[] ans = new int[size];
        int ansIndex = 0;
        for (Map.Entry<Integer, List<Integer>> entry : ansList) {
            for (int num : entry.getValue()) {
                ans[ansIndex] = num;
                ansIndex++;
            }
        }

        return ans;
    }
}
```
- Runtime: 42 ms (Beats: 28.47%)
- Memory: 82.86 MB (Beats: 5.01%)

<br>
