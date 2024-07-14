# [LeetCode Records](../../README.md) - Question 2433 Find The Original Array of Prefix Xor

### Attempt 1: 
```java
class Solution {
    public int[] findArray(int[] pref) {
        int[] answer = new int[pref.length];

        int prevCurr = 0;
        for (int i = 0; i < pref.length; i++) {
            int curr = prevCurr ^ pref[i];
            answer[i] = curr;
            prevCurr ^= curr;
        }

        return answer;
    }
}
```
- Runtime: 2 ms (Beats: 86.59%)
- Memory: 56.69 MB (Beats: 70.69%)

<br>
