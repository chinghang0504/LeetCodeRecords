# [LeetCode Records](../../README.md) - Question 528 Random Pick with Weight

### Attempt 1: Calculate the cumulative sum and use binary search to search the target
```java
class Solution {

    private int[] arr;
    private int total;
    private Random random;
    
    public Solution(int[] w) {
        arr = new int[w.length + 1];
        arr[0] = 0;

        int cumsum = 0;
        for (int i = 0; i < w.length; i++) {
            cumsum += w[i];
            arr[i + 1] = cumsum;
        }
        total = cumsum;

        random = new Random();
    }
    
    public int pickIndex() {
        int target = random.nextInt(total);

        int low = 0;
        int high = arr.length - 1;
        while (low <= high) {
            int middle = (low + high) / 2;
            if (arr[middle] <= target && target < arr[middle + 1]) {
                return middle;
            } else if (target < arr[middle]) {
                high = middle - 1;
            } else {
                low = middle + 1;
            }
        }

        return 0;
    }
}

/**
 * Your Solution object will be instantiated and called as such:
 * Solution obj = new Solution(w);
 * int param_1 = obj.pickIndex();
 */
```
- Runtime: 23 ms (Beats: 98.38%)
- Memory: 49.63 MB (Beats: 75.47%)

<br>
