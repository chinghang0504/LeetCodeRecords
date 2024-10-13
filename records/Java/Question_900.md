# [LeetCode Records](../../README.md) - Question 900 RLE Iterator

### Attempt 1: Track the current number index and the current number count
```java
class RLEIterator {

    private int[] encoding;
    private int countIndex;
    private int count;

    public RLEIterator(int[] encoding) {
        this.encoding = encoding;
        this.countIndex = 0;
        this.count = 0;
    }

    public int next(int n) {
        if (countIndex >= encoding.length) {
            return -1;
        }

        while (n > 0) {
            while (count >= encoding[countIndex]) {
                countIndex += 2;
                count = 0;
                
                if (countIndex >= encoding.length) {
                    return -1;
                }
            }

            int step = Math.min(n, encoding[countIndex] - count);
            n -= step;
            count += step;
        }

        return encoding[countIndex + 1];
    }
}

/**
 * Your RLEIterator object will be instantiated and called as such:
 * RLEIterator obj = new RLEIterator(encoding);
 * int param_1 = obj.next(n);
 */
```
- Runtime: 4 ms (Beats: 99.48%)
- Memory: 43.16 MB (Beats: 11.52%)

<br>
