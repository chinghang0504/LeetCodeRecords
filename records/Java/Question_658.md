# [LeetCode Records](../../README.md) - Question 658 Find K Closest Elements

### Attempt 1: Add k elements in the list first
```java
class Solution {
    public List<Integer> findClosestElements(int[] arr, int k, int x) {
        List<int[]> list = new LinkedList<>();
        for (int i = 0; i < k; i++) {
            list.add(new int[]{ arr[i], Math.abs(x - arr[i]) });
        }

        for (int i = k; i < arr.length; i++) {
            int diff = Math.abs(x - arr[i]);
            int[] firstItem = list.getFirst();
            if (diff < firstItem[1]) {
                list.removeFirst();
                list.add(new int[]{ arr[i], diff});
            } else if (diff > firstItem[1] || arr[i] > x) {
                break;
            }
        }

        return list.stream().map((item) -> item[0]).toList();
    }
}
```
- Runtime: 14 ms (Beats: 30.50%)
- Memory: 46.50 MB (Beats: 6.49%)

<br>

### Attempt 2: Find the start index and the end index first
```java
class Solution {
    public List<Integer> findClosestElements(int[] arr, int k, int x) {
        int startIndex = 0;
        int endIndex = arr.length - 1;

        while (endIndex - startIndex >= k) {
            int diff1 = Math.abs(x - arr[startIndex]);
            int diff2 = Math.abs(x - arr[endIndex]);
            if (diff1 > diff2) {
                startIndex++;
            } else if (diff1 < diff2) {
                endIndex--;
            } else {
                endIndex--;
            }
        }

        List<Integer> ans = new ArrayList<>();
        for (int i = startIndex; i <= endIndex; i++) {
            ans.add(arr[i]);
        }

        return ans;
    }
}
```
- Runtime: 4 ms (Beats: 96.01%)
- Memory: 45.83 MB (Beats: 60.52%)

<br>
