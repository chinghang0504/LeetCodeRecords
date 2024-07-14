# [LeetCode Records](../../README.md) - Question 1282 Group the People Given the Group Size They Belong To

### Attempt 1: Use a HashMap to save the current different sizes of groups
```java
class Solution {
    public List<List<Integer>> groupThePeople(int[] groupSizes) {
        Map<Integer, List<Integer>> map = new HashMap<>();
        List<List<Integer>> answer = new ArrayList<>();

        for (int i = 0; i < groupSizes.length; i++) {
            int size = groupSizes[i];
            List<Integer> list = map.get(size);

            if (list == null) {
                list = new ArrayList<>();
                map.put(size, list);
            }

            list.add(i);

            if (list.size() == size) {
                answer.add(list);
                map.remove(size);
            }
        }

        return answer;
    }
}
```
- Runtime: 5 ms (Beats: 92.60%)
- Memory: 45.40 MB (Beats: 15.36%)

<br>
