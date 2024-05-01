# [LeetCode Records](../../README.md) - Question 350 Intersection of Two Arrays II

### Attempt 1: Use an int array to record and an ArrayList for temporary save
```java
class Solution {
    public int[] intersect(int[] nums1, int[] nums2) {
        int[] saved = new int[1001];
        for (int i : nums1) {
            saved[i]++;
        }

        List<Integer> list = new ArrayList<>();
        for (int i : nums2) {
            if (saved[i] != 0) {
                list.add(i);
                saved[i]--;
            }
        }

        int size = list.size();
        Iterator<Integer> iterator = list.iterator();
        int[] result = new int[size];
        for (int i = 0; i < size; i++) {
            result[i] = iterator.next();
        }
        return result;
    }
}
```
- Runtime: 1 ms (Beats: 97.80%)
- Memory: 43.29 MB (Beats: 41.84%)

<br>

### Attempt 2: Use an int array to replace an ArrayList
```java
class Solution {
    public int[] intersect(int[] nums1, int[] nums2) {
        int[] saved = new int[1001];
        for (int i : nums1) {
            saved[i]++;
        }

        int[] numSaved = new int[nums2.length];
        int curr = 0;
        for (int i : nums2) {
            if (saved[i] != 0) {
                numSaved[curr++] = i;
                saved[i]--;
            }
        }

        return Arrays.copyOf(numSaved, curr);
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 43.43 MB (Beats: 24.50%)

<br>
