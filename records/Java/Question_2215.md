# [LeetCode Records](../../README.md) - Question 2215 Find the Difference of Two Arrays

### Attempt 1: Use two boolean[]
```java
class Solution {
    public List<List<Integer>> findDifference(int[] nums1, int[] nums2) {
        boolean[] arr1 = new boolean[2001];
        for(int num : nums1) {
            arr1[num + 1000] = true;
        }

        boolean[] arr2 = new boolean[2001];
        for(int num : nums2) {
            arr2[num + 1000] = true;
        }

        List<Integer> list1 = new ArrayList<>();
        for (int num : nums1) {
            if (!arr2[num + 1000]) {
                list1.add(num);
                arr2[num + 1000] = true;
            }
        }

        List<Integer> list2 = new ArrayList<>();
        for (int num : nums2) {
            if (!arr1[num + 1000]) {
                list2.add(num);
                arr1[num + 1000] = true;
            }
        }

        return List.of(list1, list2);
    }
}
```
- Runtime: 2 ms (Beats: 99.72%)
- Memory: 45.07 MB (Beats: 90.27%)

<br>
