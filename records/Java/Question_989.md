# [LeetCode Records](../../README.md) - Question 989 Add to Array-Form of Integer

### Attempt 1: Use two int[] to save the numbers
```java
class Solution {
    public List<Integer> addToArrayForm(int[] num, int k) {
        int n = 10001;
        int[] arr1 = new int[n];
        int[] arr2 = new int[n];

        for (int i = num.length - 1, j = n - 1; i >= 0; i--, j--) {
            arr1[j] = num[i];
        }

        for (int i = n - 1; k > 0; i--) {
            arr2[i] = k % 10;
            k /= 10;
        }

        int plusOne = 0;
        for (int i = n - 1; i >= 0; i--) {
            int val = arr1[i] + arr2[i] + plusOne;
            if (val >= 10) {
                val -= 10;
                plusOne = 1;
            } else {
                plusOne = 0;
            }
            arr1[i] = val;
        }

        List<Integer> answer = new ArrayList<>();
        int i = 0;
        while (arr1[i] == 0) {
            i++;
        }
        for (; i < arr1.length; i++) {
            answer.add(arr1[i]);
        }

        return answer;
    }
}
```
- Runtime: 6 ms (Beats: 31.68%)
- Memory: 46.16 MB (Beats: 8.33%)

<br>
