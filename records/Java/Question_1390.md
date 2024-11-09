# [LeetCode Records](../../README.md) - Question 1390 Four Divisors

### Attempt 1: Use an int[] as a cache
```java
class Solution {

    public int sumFourDivisors(int[] nums) {
        int[] cache = new int[100001];
        int sum = 0;

        for (int num : nums) {
            if (cache[num] == 0) {
                int[] numOfDivisors = getNumOfDivisors(num);
                if (numOfDivisors[0] == 4) {
                    cache[num] = numOfDivisors[1];
                    sum += numOfDivisors[1];
                } else {
                    cache[num] = -1;
                }
            } else if (cache[num] > 0) {
                sum += cache[num];
            }
        }

        return sum;
    }

    private int[] getNumOfDivisors(int num) {
        int numOfDivisors = 0;
        int sumOfDivisors = 0;

        int num1 = 1;
        int num2 = num;
        while (num1 < num2) {
            if (num % num1 == 0) {
                numOfDivisors += 2;
                sumOfDivisors += num1 + num2;
            }

            num1++;
            num2 = num / num1;
        }
        if (num1 == num2 && num % num1 == 0) {
            numOfDivisors++;
            sumOfDivisors += num1;
        }

        return new int[]{ numOfDivisors, sumOfDivisors };
    }
}
```
- Runtime: 37 ms (Beats: 41.78%)
- Memory: 45.04 MB (Beats: 34.02%)

<br>
