# [LeetCode Records](../../README.md) - Question 2032 Two Out of Three

### Attempt 1: Use an int[] and a HashSet
```java
class Solution {
    public List<Integer> twoOutOfThree(int[] nums1, int[] nums2, int[] nums3) {
        int[] counts = new int[101];
        Set<Integer> set = new HashSet<>();

        for (int num : nums1) {
            if (!set.contains(num)) {
                counts[num]++;
                set.add(num);
            }
        }

        set.clear();
        for (int num : nums2) {
            if (!set.contains(num)) {
                counts[num]++;
                set.add(num);
            }
        }

        set.clear();
        for (int num : nums3) {
            if (!set.contains(num)) {
                counts[num]++;
                set.add(num);
            }
        }

        List<Integer> list = new ArrayList<>();
        for (int i = 1; i < 101; i++) {
            if (counts[i] >= 2) {
                list.add(i);
            }
        }

        return list;
    }
}
```
- Runtime: 5 ms (Beats: 53.25%)
- Memory: 44.70 MB (Beats: 59.04%)

<br>
