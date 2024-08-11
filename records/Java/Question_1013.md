# [LeetCode Records](../../README.md) - Question 1013 Partition Array Into Three Parts With Equal Sum

### Attempt 1: Use a nested loop to get the sum of the subarrays
```java
class Solution {
    public boolean canThreePartsEqualSum(int[] arr) {
        int sum = 0;
        for (int num : arr) {
            sum += num;
        }
        if (sum % 3 != 0) {
            return false;
        }

        int target = sum / 3;
        int index = 0;
        for (int i = 0; i < 3; i++) {
            if (index == arr.length) {
                return false;
            }

            int localSum = arr[index];
            index++;

            while (index < arr.length && localSum != target) {
                localSum += arr[index];
                index++;
            }

            if (localSum != target) {
                return false;
            }
        }

        return true;
    }
}
```
- Runtime: 2 ms (Beats: 51.95%)
- Memory: 53.65 MB (Beats: 35.86%)

<br>
