# [LeetCode Records](../../README.md) - Question 1433 Check If a String Can Break Another String

### Attempt 1: Use Arrays.sort() to sort the char[]
```java
class Solution {
    public boolean checkIfCanBreak(String s1, String s2) {
        char[] arr1 = s1.toCharArray();
        char[] arr2 = s2.toCharArray();
        Arrays.sort(arr1);
        Arrays.sort(arr2);
        
        int size = arr1.length;
        boolean canBreak = true;
        for (int i = 0; i < size; i++) {
            if (arr1[i] > arr2[i]) {
                canBreak = false;
                break;
            }
        }
        if (canBreak) {
            return true;
        }

        canBreak = true;
        for (int i = 0; i < size; i++) {
            if (arr1[i] < arr2[i]) {
                canBreak = false;
                break;
            }
        }

        return canBreak;
    }
}
```
- Runtime: 7 ms (Beats: 83.33%)
- Memory: 45.31 MB (Beats: 50.52%)

<br>
