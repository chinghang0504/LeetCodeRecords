# [LeetCode Records](../../README.md) - Question 1860 Incremental Memory Leak

### Attempt 1: Simulate the process
```java
class Solution {
    public int[] memLeak(int memory1, int memory2) {
        int i = 1;
        
        while (true) {
            if (memory1 >= memory2) {
                if (memory1 - i >= 0) {
                    memory1 -= i;
                    i++;
                } else {
                    break;
                }
            } else {
                if (memory2 - i >= 0) {
                    memory2 -= i;
                    i++;
                } else {
                    break;
                }
            }
        }

        return new int[]{ i, memory1, memory2 };
    }
}
```
- Runtime: 3 ms (Beats: 99.06%)
- Memory: 41.06 MB (Beats: 66.04%)

<br>
