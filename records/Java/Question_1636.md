# [LeetCode Records](../../README.md) - Question 1636 Sort Array by Increasing Frequency

### Attempt 1: Use Arrays.sort() and Comparator
```java
class Solution {
    public int[] frequencySort(int[] nums) {
        int[] counts = new int[201];

        for (int num : nums) {
            counts[num + 100]++;
        }

        Integer[] integerArray = Arrays.stream(nums).boxed().toArray(Integer[]::new);
        Arrays.sort(integerArray, new Comparator<Integer>() {
            @Override
            public int compare(Integer o1, Integer o2) {
                int count1 = counts[o1 + 100];
                int count2 = counts[o2 + 100];
                if (count1 < count2) {
                    return -1;
                } else if (count1 > count2) {
                    return 1;
                }

                if (o1 > o2) {
                    return -1;
                } else if (o1 < o2) {
                    return 1;
                } else {
                    return 0;
                }
            }
        });

        return Arrays.stream(integerArray).mapToInt(Integer::intValue).toArray();
    }
}
```
- Runtime: 8 ms (Beats: 51.78%)
- Memory: 44.65 MB (Beats: 21.57%)

<br>
