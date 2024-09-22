# [LeetCode Records](../../README.md) - Question 946 Validate Stack Sequences

### Attempt 1: Use a LinkedList to store the pushed numbers
```java
class Solution {
    public boolean validateStackSequences(int[] pushed, int[] popped) {
        int size = pushed.length;
        int leftIndex = 0;
        int rightIndex = 0;
        List<Integer> list = new LinkedList<>();

        while (leftIndex < size && rightIndex < size) {
            if (pushed[leftIndex] == popped[rightIndex]) {
                leftIndex++;
                rightIndex++;
            } else {
                while (!list.isEmpty() && rightIndex < size && list.getLast() == popped[rightIndex]) {
                    list.removeLast();
                    rightIndex++;
                }

                if (leftIndex < size) {
                    list.add(pushed[leftIndex]);
                    leftIndex++;
                }
            }
        }

        while (!list.isEmpty() && rightIndex < size && list.getLast() == popped[rightIndex]) {
            list.removeLast();
            rightIndex++;
        }

        return leftIndex == size && rightIndex == size;
    }
}
```
- Runtime: 1 ms (Beats: 95.40%)
- Memory: 44.42 MB (Beats: 24.02%)

<br>
