# [LeetCode Records](../../README.md) - Question 1213 Intersection of Three Sorted Arrays

### Attempt 1: Use three HashSet
```java
class Solution {
    public List<Integer> arraysIntersection(int[] arr1, int[] arr2, int[] arr3) {
        Set<Integer> set1 = new HashSet<>();
        Set<Integer> set2 = new HashSet<>();
        Set<Integer> set3 = new HashSet<>();

        for (int num : arr1) {
            set1.add(num);
        }
        for (int num : arr2) {
            set2.add(num);
        }
        for (int num : arr3) {
            set3.add(num);
        }

        List<Integer> result = new ArrayList<>();
        for (int num : set1) {
            if (set2.contains(num) && set3.contains(num)) {
                result.add(num);
            }
        }

        result.sort((a, b) -> a - b);

        return result;
    }
}
```
- Runtime: 8 ms (Beats: 16.96%)
- Memory: 45.08 MB (Beats: 9.54%)

<br>
