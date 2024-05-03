# [LeetCode Records](../../README.md) - Question 760 Find Anagram Mappings

### Attempt 1: Use a HashMap
```java
class Solution {
    public int[] anagramMappings(int[] nums1, int[] nums2) {
        Map<Integer, Integer> map = new HashMap<>();
        for (int i = 0; i < nums2.length; i++) {
            map.put(nums2[i], i);
        }

        int[] result = new int[nums1.length];
        for (int i = 0; i < nums1.length; i++) {
            result[i] = map.get(nums1[i]);
        }

        return result;
    }
}
```
- Runtime: 1 ms (Beats: 98.80%)
- Memory: 41.20 MB (Beats: 98.80%)

<br>

### Attempt 2: Modify the original array
```java
class Solution {
    public int[] anagramMappings(int[] nums1, int[] nums2) {
        Map<Integer, Integer> map = new HashMap<>(nums2.length);
        for (int i = 0; i < nums2.length; i++) {
            map.put(nums2[i], i);
        }

        for (int i = 0; i < nums1.length; i++) {
            nums1[i] = map.get(nums1[i]);
        }

        return nums1;
    }
}
```
- Runtime: 1 ms (Beats: 98.80%)
- Memory: 41.22 MB (Beats: 98.80%)

<br>
