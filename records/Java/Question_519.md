# [LeetCode Records](../../README.md) - Question 519 Random Flip Matrix

### Attempt 1: Use a HashSet to store the flipped positions
```java
class Solution {

    private int m;
    private int n;
    private Random random;
    private Set<String> set;

    public Solution(int m, int n) {
        this.m = m;
        this.n = n;
        this.random = new Random();
        this.set = new HashSet<>();
    }
    
    public int[] flip() {
        int x = random.nextInt(m);
        int y = random.nextInt(n);
        String str = x + " " + y;

        while (set.contains(str)) {
            x = random.nextInt(m);
            y = random.nextInt(n);
            str = x + " " + y;
        }

        set.add(str);
        return new int[]{ x, y };
    }
    
    public void reset() {
        set = new HashSet<>();
    }
}

/**
 * Your Solution object will be instantiated and called as such:
 * Solution obj = new Solution(m, n);
 * int[] param_1 = obj.flip();
 * obj.reset();
 */
```
- Runtime: 28 ms (Beats: 29.03%)
- Memory: 45.59 MB (Beats: 45.04%)

<br>
