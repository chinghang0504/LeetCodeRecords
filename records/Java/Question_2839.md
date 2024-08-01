# [LeetCode Records](../../README.md) - Question 2839 Check if Strings Can be Made Equal With Operations I

### Attempt 1: Use a helper function to sort the array
```java
class Solution {
    public boolean canBeEqual(String s1, String s2) {
        char[] arr1 = s1.toCharArray();
        char[] arr2 = s2.toCharArray();
        
        sortArr(arr1);
        sortArr(arr2);

        for (int i = 0; i < 4; i++) {
            if (arr1[i] != arr2[i]) {
                return false;
            }
        }

        return true;
    }

    private void sortArr(char[] arr) {
        if (arr[0] > arr[2]) {
            char temp = arr[0];
            arr[0] = arr[2];
            arr[2] = temp;
        }
        if (arr[1] > arr[3]) {
            char temp = arr[1];
            arr[1] = arr[3];
            arr[3] = temp;
        }
    }
}
```
- Runtime: 1 ms (Beats: 96.52%)
- Memory: 42.42 MB (Beats: 77.39%)

<br>
