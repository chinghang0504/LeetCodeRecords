# [LeetCode Records](../../README.md) - Question 1243 Array Transformation

### Attempt 1: Use a while loop until the array is unchanged
```java
class Solution {
    public List<Integer> transformArray(int[] arr) {
        boolean isChanged = true;
        while (isChanged) {
            int[] nextArr = arr.clone();
            isChanged = false;

            for (int i = 1; i < arr.length - 1; i++) {
                if (arr[i] < arr[i - 1] && arr[i] < arr[i + 1]) {
                    nextArr[i]++;
                    isChanged = true;
                } else if (arr[i] > arr[i - 1] && arr[i] > arr[i + 1]) {
                    nextArr[i]--;
                    isChanged = true;
                }
            }

            arr = nextArr;
        }

        List<Integer> answer = new ArrayList<>();
        for (int num : arr) {
            answer.add(num);
        }

        return answer;
    }
}
```
- Runtime: 1 ms (Beats: 98.00%)
- Memory: 41.80 MB (Beats: 40.00%)

<br>
