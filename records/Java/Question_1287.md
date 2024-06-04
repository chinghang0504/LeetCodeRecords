# [LeetCode Records](../../README.md) - Question 1287 Element Appearing More Than 25% In Sorted Array

### Attempt 1: Count every number
```java
class Solution {
    public int findSpecialInteger(int[] arr) {
        double target = arr.length * 0.25;
        
        int count = 1;
        for (int i = 1; i < arr.length; i++) {
            if (arr[i] == arr[i - 1]) {
                count++;
                if (count > target) {
                    return arr[i];
                }
            } else {
                count = 1;
            }
        }

        return arr[0];
    }
}
```
- Runtime: 1 ms (Beats: 49.72%)
- Memory: 44.41 MB (Beats: 88.33%)

<br>
