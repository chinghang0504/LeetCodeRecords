# [LeetCode Records](../../README.md) - Question 2120 Execution of All Suffix Instructions Staying in a Grid

### Attempt 1: Test each case
```java
class Solution {
    public int[] executeInstructions(int n, int[] startPos, String s) {
        char[] arr = s.toCharArray();
        int[] ans = new int[arr.length];

        for (int i = 0; i < arr.length; i++) {
            ans[i] = getInstructionNum(n, startPos, arr, i);
        }

        return ans;
    }

    private int getInstructionNum(int n, int[] startPos, char[] arr, int arrStartIndex) {
        int i = startPos[0];
        int j = startPos[1];
        int count = 0;
        
        for (int arrIndex = arrStartIndex; arrIndex < arr.length; arrIndex++) {
            if (arr[arrIndex] == 'U') {
                i--;
            } else if (arr[arrIndex] == 'D') {
                i++;
            } else if (arr[arrIndex] == 'L') {
                j--;
            } else {
                j++;
            }

            if (i < 0 || i >= n || j < 0 || j >= n) {
                break;
            }

            count++;
        }

        return count;
    }
}
```
- Runtime: 13 ms (Beats: 96.02%)
- Memory: 44.60 MB (Beats: 72.14%)

<br>
