# [LeetCode Records](../../README.md) - Question 2956 Find Common Elements Between Two Arrays

### Attempt 1: Use two HashSet
```java
class Solution {
    public int[] findIntersectionValues(int[] nums1, int[] nums2) {
        Set<Integer> set1 = new HashSet<>();
        for (int num : nums1) {
            set1.add(num);
        }
        int answer2 = 0;
        for (int num : nums2) {
            if (set1.contains(num)) {
                answer2++;
            }
        }

        Set<Integer> set2 = new HashSet<>();
        for (int num : nums2) {
            set2.add(num);
        }
        int answer1 = 0;
        for (int num : nums1) {
            if (set2.contains(num)) {
                answer1++;
            }
        }

        return new int[]{answer1, answer2};
    }
}
```
- Runtime: 6 ms (Beats: 66.24%)
- Memory: 45.39 MB (Beats: 53.64%)

<br>
