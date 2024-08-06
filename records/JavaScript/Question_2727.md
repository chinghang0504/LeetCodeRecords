# [LeetCode Records](../../README.md) - Question 2727 Is Object Empty

### Attempt 1: Use Object.keys()
```js
/**
 * @param {Object|Array} obj
 * @return {boolean}
 */
var isEmpty = function(obj) {
    return Object.keys(obj).length === 0;
};
```
- Runtime: 45 ms (Beats: 88.98%)
- Memory: 49.55 MB (Beats: 21.29%)

<br>
