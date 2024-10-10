# [LeetCode Records](../../README.md) - Question 3106 Lexicographically Smallest String After Operations With Constraint

### Attempt 1: Calculate two differences to the character a for each character
```java
class Solution {
    public String getSmallestString(String s, int k) {
        char[] arr = s.toCharArray();

        int i = 0;
        while (k > 0 && i < arr.length) {
            int diff1 = arr[i] - 'a';
            int diff2 = 26 - diff1;

            if (diff2 > k) {
                int diff = Math.min(diff1, k);
                arr[i] = (char)(arr[i] - diff);
                k -= diff;
            } else {
                if (diff1 <= diff2) {
                    arr[i] = (char)(arr[i] - diff1);
                    k -= diff1;
                } else {
                    arr[i] = (char)(arr[i] + diff2 - 26);
                    k -= diff2;
                }
            }

            i++;
        }

        return new String(arr);
    }
}
```
- Runtime: 1 ms (Beats: 100.00%)
- Memory: 42.09 MB (Beats: 99.27%)

<br>
