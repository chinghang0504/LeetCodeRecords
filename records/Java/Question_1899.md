# [LeetCode Records](../../README.md) - Question 1899 Merge Triplets to Form Target Triplet

### Attempt 1: Ignore the triplet if any element is larger than the corresponding target element
```java
class Solution {
    public boolean mergeTriplets(int[][] triplets, int[] target) {
        int[] maxArr = new int[3];

        for (int[] triplet : triplets) {
            if (triplet[0] > target[0] || triplet[1] > target[1] || triplet[2] > target[2]) {
                continue;
            }

            for (int i = 0; i < 3; i++) {
                maxArr[i] = Math.max(maxArr[i], triplet[i]);
            }
        }

        if (maxArr[0] != target[0] || maxArr[1] != target[1] || maxArr[2] != target[2]) {
            return false;
        }

        return true;
    }
}
```
- Runtime: 5 ms (Beats: 67.81%)
- Memory: 119.34 MB (Beats: 68.14%)

<br>
