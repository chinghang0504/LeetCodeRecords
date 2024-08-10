# [LeetCode Records](../../README.md) - Question 914 X of a Kind in a Deck of Cards

### Attempt 1: Use a nested loop to find the common factor of counts
```java
class Solution {
    public boolean hasGroupsSizeX(int[] deck) {
        int[] counts = new int[10000];

        for (int num : deck) {
            counts[num]++;
        }

        List<Integer> list = new ArrayList<>();
        int minCount = Integer.MAX_VALUE;
        for (int i = 0; i < 10000; i++) {
            if (counts[i] != 0) {
                list.add(counts[i]);
                minCount = Math.min(minCount, counts[i]);
            }
        }

        for (int i = 2; i <= minCount; i++) {
            boolean isCommonFactor = true;
            for (int count : list) {
                if (count % i != 0) {
                    isCommonFactor = false;
                    break;
                }
            }

            if (isCommonFactor) {
                return true;
            }
        }

        return false;
    }
}
```
- Runtime: 3 ms (Beats: 92.24%)
- Memory: 45.02 MB (Beats: 84.11%)

<br>
