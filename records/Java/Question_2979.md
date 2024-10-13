# [LeetCode Records](../../README.md) - Question 2979 Most Expensive Item That Can Not Be Bought

### Attempt 1: Test every possible case
```java
class Solution {
    public int mostExpensiveItem(int primeOne, int primeTwo) {
        int max = primeOne * primeTwo;
        boolean[] nums = new boolean[max + 1];

        int[] arr1 = new int[primeTwo];
        int size1 = 0;
        for (int i = 1; i <= primeTwo; i++) {
            int num = primeOne * i;
            arr1[size1] = num;
            size1++;
            nums[num] = true;
        }

        int[] arr2 = new int[primeOne];
        int size2 = 0;
        for (int i = 1; i <= primeOne; i++) {
            int num = primeTwo * i;
            arr2[size2] = num;
            size2++;
            nums[num] = true;
        }

        for (int i = 0; i < arr1.length; i++) {
            for (int j = 0; j < arr2.length; j++) {
                int num = arr1[i] + arr2[j];
                if (num >= max) {
                    break;
                } else {
                    nums[num] = true;
                }
            }
        }

        for (int i = max; i >= 0; i--) {
            if (!nums[i]) {
                return i;
            }
        }
        
        return 0;
    }
}
```
- Runtime: 11 ms (Beats: 53.29%)
- Memory: 44.20 MB (Beats: 48.78%)

<br>

### Attempt 2: Use Chicken McNugget Theorem (m * n - m - n)
```java
class Solution {
    public int mostExpensiveItem(int primeOne, int primeTwo) {
        return primeOne * primeTwo - primeOne - primeTwo;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 40.48 MB (Beats: 95.37%)

<br>
