# [LeetCode Records](../../README.md) - Question 1248 Count Number of Nice Subarrays

### Attempt 1: Use an ArrayList to store the odd number indices
```java
class Solution {
    public int numberOfSubarrays(int[] nums, int k) {
        List<Integer> list = new ArrayList<>();
        list.add(-1);
        for (int i = 0; i < nums.length; i++) {
            if (nums[i] % 2 == 1) {
                list.add(i);
            }
        }
        list.add(nums.length);

        int count = 0;
        int end = list.size() - 1 - k;
        for (int i = 1; i <= end; i++) {
            int prevIndex = list.get(i - 1);
            int firstIndex = list.get(i);
            int lastIndex = list.get(i + k - 1);
            int nextIndex = list.get(i + k);

            int firstCount = firstIndex - prevIndex;
            int lastCount = nextIndex - lastIndex;
            count += firstCount * lastCount;
        }

        return count;
    }
}
```
- Runtime: 10 ms (Beats: 78.08%)
- Memory: 54.04 MB (Beats: 89.26%)

<br>

### Attempt 2: Use an int[] to store the odd number indices
```java
class Solution {
    public int numberOfSubarrays(int[] nums, int k) {
        int[] oddNumIndices = new int[nums.length + 2];
        int size = 1;

        oddNumIndices[0] = -1;
        for (int i = 0; i < nums.length; i++) {
            if (nums[i] % 2 == 1) {
                oddNumIndices[size] = i;
                size++;
            }
        }
        oddNumIndices[size] = nums.length;
        size++;

        int count = 0;
        for (int i = 1; i < size - k; i++) {
            int prevIndex = oddNumIndices[i - 1];
            int firstIndex = oddNumIndices[i];
            int lastIndex = oddNumIndices[i + k - 1];
            int nextIndex = oddNumIndices[i + k];

            int firstCount = firstIndex - prevIndex;
            int lastCount = nextIndex - lastIndex;
            count += firstCount * lastCount;
        }

        return count;
    }
}
```
- Runtime: 6 ms (Beats: 93.40%)
- Memory: 52.16 MB (Beats: 98.86%)

<br>
