# [LeetCode Records](../../README.md) - Question 1630 Arithmetic Subarrays

### Attempt 1: Sort the array and test if it is arithmetic
```java
class Solution {
    public List<Boolean> checkArithmeticSubarrays(int[] nums, int[] l, int[] r) {
        List<Boolean> ans = new ArrayList<>();
        int size = l.length;

        for (int i = 0; i < size; i++) {
            int[] arr = getSortedSubarray(nums, l[i], r[i] + 1);
            ans.add(isArithmetic(arr));
        }
        
        return ans;
    }

    private int[] getSortedSubarray(int[] nums, int start, int end) {
        int[] arr = Arrays.copyOfRange(nums, start, end);
        Arrays.sort(arr);
        return arr;
    }

    private boolean isArithmetic(int[] arr) {
        if (arr.length == 1 || arr.length == 2) {
            return true;
        }

        int diff = arr[1] - arr[0];
        for (int i = 2; i < arr.length; i++) {
            if (arr[i] - arr[i - 1] != diff) {
                return false;
            }
        }

        return true;
    }
}
```
- Runtime: 17 ms (Beats: 81.66%)
- Memory: 45.07 MB (Beats: 90.93%)

<br>
