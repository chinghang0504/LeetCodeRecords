# [LeetCode Records](../../README.md) - Question 2665 Counter II

### Attempt 1: 
```js
var createCounter = function(init) {
    let val = init;

    return {
        increment: function() {
            val++;
            return val;
        },
        decrement: function() {
            val--;
            return val;
        },
        reset: function() {
            val = init;
            return val;
        }
    }
};
```
- Runtime: 51 ms (Beats: 90.61%)
- Memory: 51.45 MB (Beats: 70.26%)

<br>
