# [LeetCode Records](../../README.md) - Question 2620 Counter

### Attempt 1: 
```js
var createCounter = function(n) {
    n--;
    return function() {
        n++;
        return n;
    }
}
```
- Runtime: 35 ms (Beats: 99.40%)
- Memory: 48.21 MB (Beats: 92.32%)

<br>
