# [LeetCode Records](../../README.md) - Question 2724 Sort By

### Attempt 1: Use sort()
```js
var sortBy = function(arr, fn) {
    return arr.sort((a, b) => {
        return fn(a) - fn(b);
    });
};
```
- Runtime: 109 ms (Beats: 98.35%)
- Memory: 65.24 MB (Beats: 75.30%)

<br>
