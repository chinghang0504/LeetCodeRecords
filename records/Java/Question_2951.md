# [LeetCode Records](../../README.md) - Question 2951 Find the Peaks

### Attempt 1: Compare the previous and the next heights
```java
class Solution {
    public List<Integer> findPeaks(int[] mountain) {
        List<Integer> peaks = new ArrayList<>();

        for (int i = 1; i < mountain.length - 1; i++) {
            if (mountain[i] > mountain[i - 1] && mountain[i] > mountain[i + 1]) {
                peaks.add(i);
            }
        }

        return peaks;
    }
}
```
- Runtime: 1 ms (Beats: 100.00%)
- Memory: 43.92 MB (Beats: 27.43%)

<br>
