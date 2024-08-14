# [LeetCode Records](../../README.md) - Question 1442 Count Triplets That Can Form Two Arrays of Equal XOR

### Attempt 1: Use a nested loop to test every case
```java
class Solution {
    public int countTriplets(int[] arr) {
        int count = 0;

        for (int i = 0; i < arr.length - 1; i++) {
            for (int j = i + 1; j < arr.length; j++) {
                for (int k = j; k < arr.length; k++) {
                    if (isValidTriplet(arr, i, j, k)) {
                        count++;
                    }
                }
            }
        }

        return count;
    }

    private boolean isValidTriplet(int[] arr, int n1, int n2, int n3) {
        int a = arr[n1];
        for (int i = n1 + 1; i < n2; i++) {
            a ^= arr[i];
        }

        int b = arr[n2];
        for (int i = n2 + 1; i <= n3; i++) {
            b ^= arr[i];
        }

        return a == b;
    }
}
```
- Runtime: 2226 ms (Beats: 5.08%)
- Memory: 40.83 MB (Beats: 84.18%)

<br>
