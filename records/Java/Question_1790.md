# [LeetCode Records](../../README.md) - Question 1790 Check if One String Swap Can Make Strings Equal

### Attempt 1: Compare each character in both arrays
```java
class Solution {
    public boolean areAlmostEqual(String s1, String s2) {
        char[] arr1 = s1.toCharArray();
        char[] arr2 = s2.toCharArray();
        int size = 0;
        char[] saved = new char[4];

        int count = 0;
        for (int i = 0; i < arr1.length; i++) {
            if (arr1[i] != arr2[i]) {
                count++;

                if (count > 2) {
                    return false;
                }

                saved[size] = arr1[i];
                saved[size + 1] = arr2[i];
                size += 2;
            }
        }

        return saved[0] == saved[3] && saved[1] == saved[2];
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 41.32 MB (Beats: 73.33%)

<br>
