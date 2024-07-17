# [LeetCode Records](../../README.md) - Question 1046 Last Stone Weight

### Attempt 1: Use a loop and Arrays.sort()
```java
class Solution {
    public int lastStoneWeight(int[] stones) {
        int stoneNum = stones.length;

        while (stoneNum != 0 && stoneNum != 1) {
            Arrays.sort(stones, 0, stoneNum);
            
            int stoneWeight1 = stones[stoneNum - 2];
            int stoneWeight2 = stones[stoneNum - 1];
            if (stoneWeight1 == stoneWeight2) {
                stoneNum -= 2;
            } else {
                stones[stoneNum - 2] = stoneWeight2 - stoneWeight1;
                stoneNum--;
            }
        }

        return stoneNum == 0 ? 0 : stones[0];
    }
}
```
- Runtime: 1 ms (Beats: 98.57%)
- Memory: 40.88 MB (Beats: 61.60%)

<br>
