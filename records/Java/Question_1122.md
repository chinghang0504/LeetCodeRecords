# [LeetCode Records](../../README.md) - Question 1122 Relative Sort Array

### Attempt 1: Use a HashMap and Arrays.sort()
```java
class Solution {
    public int[] relativeSortArray(int[] arr1, int[] arr2) {
        Map<Integer, Integer> map = new HashMap<>();

        for (int i = 0; i < arr2.length; i++) {
            map.put(arr2[i], i);
        }

        Integer[] integerArray = Arrays.stream(arr1).boxed().toArray(Integer[]::new);
        Arrays.sort(integerArray, new Comparator<Integer>(){
            @Override
            public int compare(Integer o1, Integer o2) {
                Integer val1 = map.get(o1);
                Integer val2 = map.get(o2);

                if (val1 != null && val2 != null) {
                    return val1 - val2;
                } else if (val1 != null) {
                    return -1;
                } else if (val2 != null) {
                    return 1;
                } else {
                    return o1 - o2;
                }
            }
        });

        return Arrays.stream(integerArray).mapToInt(Integer::intValue).toArray();
    }
}
```
- Runtime: 5 ms (Beats: 12.33%)
- Memory: 41.85 MB (Beats: 69.58%)

<br>
