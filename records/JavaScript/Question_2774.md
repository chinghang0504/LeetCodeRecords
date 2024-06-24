# [LeetCode Records](../../README.md) - Question 2774 Array Upper Bound

### Attempt 1: Use lastIndexOf()
```js
Array.prototype.upperBound = function(target) {
    return this.lastIndexOf(target);
};
```
- Runtime: 45 ms (Beats: 94.07%)
- Memory: 51.00 MB (Beats: 77.12%)

<br>
