# [LeetCode Records](../../README.md) - Question 496 Next Greater Element I

### Attempt 1: Use a HashMap to record the index of elements in nums2
```java
class Solution {
    public int[] nextGreaterElement(int[] nums1, int[] nums2) {
        HashMap<Integer, Integer> hashMap = new HashMap<>();
        for (int i = 0; i < nums2.length; i++) {
            hashMap.put(nums2[i], i);
        }

        int[] saved = new int[nums1.length];
        int count = 0;
        for (int i = 0; i < nums1.length; i++) {
            int val = nums1[i];
            Integer index = hashMap.get(val);

            saved[count++] = -1;

            if (index != null) {
                for (int j = index + 1; j < nums2.length; j++) {
                    if (nums2[j] > val) {
                        saved[count - 1] = nums2[j];
                        break;
                    }
                }
            }
        }

        return saved;
    }
}
```
- Runtime: 2 ms (Beats: 98.80%)
- Memory: 43.13 MB (Beats: 80.10%)

<br>
