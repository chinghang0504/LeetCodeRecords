# [LeetCode Records](../../README.md) - Question 157 Read N Characters Given Read4

### Attempt 1: Use a variable to count the number of characters read
```java
public class Solution extends Reader4 {
    /**
     * @param buf Destination buffer
     * @param n   Number of characters to read
     * @return    The number of actual characters read
     */
    public int read(char[] buf, int n) {
        char[] buf4 = new char[4];
        int curr = 0;

        int readCount = read4(buf4);
        while (readCount != 0) {
            for (int i = 0; i < readCount && curr < n; i++) {
                buf[curr++] = buf4[i];
            }
            
            readCount = read4(buf4);
        }

        return curr;
    }
}
```
- Runtime: 0 ms (Beats: 100.00%)
- Memory: 41.26 MB (Beats: 69.50%)

<br>
