# [LeetCode Records](../../README.md) - Question 2094 Finding 3-Digit Even Numbers

### Attempt 1: Use Arrays.sort(), a boolean[], and an int[]
```java
class Solution {
    public int[] findEvenNumbers(int[] digits) {
        Arrays.sort(digits);

        boolean[] saved = new boolean[1000];

        for (int i = 0; i < digits.length; i++) {
            for (int j = 0; j < digits.length; j++) {
                for (int k = 0; k < digits.length; k++) {
                    if (i != j && j != k && k != i) {
                        int num = digits[i] * 100 + digits[j] * 10 + digits[k];
                        if (num >= 100 && num % 2 == 0) {
                            saved[num] = true;
                        }
                    }
                }
            }
        }

        int[] answer = new int[1000];
        int size = 0;
        for (int i = 100; i < 1000; i++) {
            if (saved[i]) {
                answer[size] = i;
                size++;
            }
        }

        return Arrays.copyOf(answer, size);
    }
}
```
- Runtime: 78 ms (Beats: 27.18%)
- Memory: 44.74 MB (Beats: 43.96%)

<br>
