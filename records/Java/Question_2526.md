# [LeetCode Records](../../README.md) - Question 2526 Find Consecutive Integers from a Data Stream

### Attempt 1: Track the current target count
```java
class DataStream {

    private int value;
    private int k;
    private int count;

    public DataStream(int value, int k) {
        this.value = value;
        this.k = k;
        this.count = 0;
    }
    
    public boolean consec(int num) {
        count = num == value ? count + 1 : 0;
        return count >= k;
    }
}

/**
 * Your DataStream object will be instantiated and called as such:
 * DataStream obj = new DataStream(value, k);
 * boolean param_1 = obj.consec(num);
 */
```
- Runtime: 25 ms (Beats: 100.00%)
- Memory: 101.54 MB (Beats: 38.21%)

<br>
