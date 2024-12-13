# [LeetCode Records](../../README.md) - Question 2075 Decode the Slanted Ciphertext

### Attempt 1: Calculate the correct index the array
```java
class Solution {
    public String decodeCiphertext(String encodedText, int rows) {
        char[] arr = encodedText.toCharArray();
        int cols = arr.length / rows;
        StringBuilder stringBuilder = new StringBuilder();

        for (int firstJ = 0; firstJ < cols; firstJ++) {
            for (int i = 0; i < rows; i++) {
                int j = i + firstJ;

                if (j < cols) {
                    stringBuilder.append(arr[i * cols + j]);
                }
            }
        }

        return stringBuilder.toString().stripTrailing();
    }
}
```
- Runtime: 30 ms (Beats: 70.15%)
- Memory: 55.46 MB (Beats: 18.92%)

<br>
