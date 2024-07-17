# [LeetCode Records](../../README.md) - Question 1652 Defuse the Bomb

### Attempt 1: Calculate the sum of each case
```java
class Solution {
    public int[] decrypt(int[] code, int k) {
        int[] answer = new int[code.length];

        for (int i = 0; i < code.length; i++) {
            answer[i] = getDecryptedCode(code, k, i);
        }

        return answer;
    }

    private int getDecryptedCode(int[] code, int k, int i) {
        if (k == 0) {
            return 0;
        } else if (k > 0) {
            int sum = 0;
            for (int j = 0; j < k; j++) {
                sum += code[getIndex(code.length, i + 1 + j)];
            }
            return sum;
        } else {
            k = Math.abs(k);
            int sum = 0;
            for (int j = 0; j < k; j++) {
                sum += code[getIndex(code.length, i - 1 - j)];
            }
            return sum;
        }
    }

    private int getIndex(int length, int i) {
        if (i >= 0 && i < length) {
            return i;
        } else if (i >= length) {
            return i - length;
        } else {
            return length + i;
        }
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 42.33 MB (Beats: 16.16%)

<br>
