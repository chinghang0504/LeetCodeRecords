# [LeetCode Records](../../README.md) - Question 1078 Occurrences After Bigram

### Attempt 1: Use split()
```java
class Solution {
    public String[] findOcurrences(String text, String first, String second) {
        String[] arr = text.split(" ");
        String[] answer = new String[1000];
        int size = 0;

        for (int i = 0; i < arr.length - 2; i++) {
            if (arr[i].equals(first) && arr[i + 1].equals(second)) {
                answer[size] = arr[i + 2];
                size++;
            }
        }

        return Arrays.copyOf(answer, size);
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 41.71 MB (Beats: 7.69%)

<br>
