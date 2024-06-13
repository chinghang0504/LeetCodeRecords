# [LeetCode Records](../../README.md) - Question 2629 Function Composition

### Attempt 1: 
```js
var compose = function(functions) {
    
    return function(x) {
        for (let i = functions.length - 1; i >= 0; i--) {
            x = functions[i](x);
        }
        return x;
    }
};
```
- Runtime: 52 ms (Beats: 96.98%)
- Memory: 50.21 MB (Beats: 28.76%)

<br>
