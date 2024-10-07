# [LeetCode Records](../../README.md) - Question 901 Online Stock Span

### Attempt 1: Search the previous prices
```java
class StockSpanner {

    private List<Integer> list;

    public StockSpanner() {
        list = new ArrayList<>();
    }
    
    public int next(int price) {
        list.addFirst(price);

        int count = 0;
        for (int prevPrice : list) {
            if (prevPrice <= price) {
                count++;
            } else {
                break;
            }
        }

        return count;
    }
}

/**
 * Your StockSpanner object will be instantiated and called as such:
 * StockSpanner obj = new StockSpanner();
 * int param_1 = obj.next(price);
 */
```
- Runtime: 1891 ms (Beats: 5.07%)
- Memory: 56.14 MB (Beats: 7.32%)

<br>
