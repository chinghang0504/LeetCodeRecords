# [LeetCode Records](../../README.md) - Question 349 Intersection of Two Arrays

### Attempt 1: Use two HashSet
```java
class Solution {
    public int[] intersection(int[] nums1, int[] nums2) {
        HashSet<Integer> hashSet1 = new HashSet<>();
        for (int i : nums1) {
            hashSet1.add(i);
        }

        HashSet<Integer> hashSet2 = new HashSet<>();
        for (int i : nums2) {
            if (hashSet1.contains(i)) {
                hashSet2.add(i);
            }
        }

        return hashSet2.stream().mapToInt(Number::intValue).toArray();
    }
}
```
- Runtime: 4 ms (Beats: 31.73%)
- Memory: 43.28 MB (Beats: 43.89%)

<br>

### Attempt 2: Use a boolean array to record and an ArrayList for temporary save
```java
class Solution {
    public int[] intersection(int[] nums1, int[] nums2) {
        boolean[] saved = new boolean[1001];
        for (int i : nums1) {
            saved[i] = true;
        }

        List<Integer> list = new ArrayList<>();
        for (int i : nums2) {
            if (saved[i]) {
                list.add(i);
                saved[i] = false;
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
- Runtime: 1 ms (Beats: 97.58%)
- Memory: 42.73 MB (Beats: 91.32%)

<br>

### Attempt 3: Use an int array to replace an ArrayList
```java
class Solution {
    public int[] intersection(int[] nums1, int[] nums2) {
        boolean[] saved = new boolean[1001];
        for (int i : nums1) {
            saved[i] = true;
        }

        int[] numSaved = new int[nums2.length];
        int curr = 0;
        for (int i : nums2) {
            if (saved[i]) {
                numSaved[curr++] = i;
                saved[i] = false;
            }
        }

        return Arrays.copyOf(numSaved, curr);
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 42.58 MB (Beats: 97.46%)

<br>
