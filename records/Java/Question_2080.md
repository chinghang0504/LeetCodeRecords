# [LeetCode Records](../../README.md) - Question 2080 Range Frequency Queries

### Attempt 1: Use a HashMap to store the integer and its list of indices
```java
class RangeFreqQuery {

    private Map<Integer, List<Integer>> map;

    public RangeFreqQuery(int[] arr) {
        map = new HashMap<>();

        for (int i = 0; i < arr.length; i++) {
            List<Integer> list = map.get(arr[i]);
            if (list == null) {
                list = new ArrayList<>();
                map.put(arr[i], list);
            }
            list.add(i);
        }
    }
    
    public int query(int left, int right, int value) {
        List<Integer> list = map.get(value);
        if (list == null) {
            return 0;
        }

        int freq1 = findTargetFreq(list, left - 1);
        int freq2 = findTargetFreq(list, right);
        return freq2 - freq1;
    }

    private int findTargetFreq(List<Integer> list, int targetIndex) {
        int size = list.size();
        int leftIndex = 0;
        int rightIndex = size - 1;
        while (leftIndex <= rightIndex) {
            int midIndex = leftIndex + (rightIndex - leftIndex) / 2;
            int index = list.get(midIndex);
            if (index == targetIndex) {
                return midIndex + 1;
            } else if (index > targetIndex) {
                rightIndex = midIndex - 1;
            } else {
                leftIndex = midIndex + 1;
            }
        }
        return leftIndex;
    }
}

/**
 * Your RangeFreqQuery object will be instantiated and called as such:
 * RangeFreqQuery obj = new RangeFreqQuery(arr);
 * int param_1 = obj.query(left,right,value);
 */
```
- Runtime: 122 ms (Beats: 98.44%)
- Memory: 132.14 MB (Beats: 92.97%)

<br>
