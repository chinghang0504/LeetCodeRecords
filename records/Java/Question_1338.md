# [LeetCode Records](../../README.md) - Question 1338 Reduce Array Size to The Half

### Attempt 1: Use a HashMap to store the number counts
```java
class Solution {
    public int minSetSize(int[] arr) {
        Map<Integer, Integer> map = new HashMap<>();
        for (int num : arr) {
            map.merge(num, 1, Integer::sum);
        }

        List<Map.Entry<Integer, Integer>> list = new ArrayList<>(map.entrySet());
        list.sort(Map.Entry.comparingByValue());

        int size = arr.length;
        int halfSize = Math.ceilDiv(size, 2);
        int count = 0;
        int i = list.size() - 1;
        while (size > halfSize) {
            int numSize = list.get(i).getValue();
            i--;
            size -= numSize;
            count++;
        }

        return count;
    }
}
```
- Runtime: 36 ms (Beats: 61.85%)
- Memory: 61.84 MB (Beats: 34.85%)

<br>
