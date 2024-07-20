# [LeetCode Records](../../README.md) - Question 1539 Kth Missing Positive Number

### Attempt 1: Use a nested loop and a while loop
```java
class Solution {
    public int findKthPositive(int[] arr, int k) {
        int curr = 1 ;
        int count = 0;

        for (int i = 0; i < arr.length; i++) {
            while (curr != arr[i]) {
                count++;
                if (count == k) {
                    return curr;
                }
                curr++;
            }
            curr++;
        }
        count++;
        
        while (count < k) {
            count++;
            curr++;
        }

        return curr;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 42.45 MB (Beats: 77.65%)

<br>
