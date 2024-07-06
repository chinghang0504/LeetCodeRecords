# [LeetCode Records](../../README.md) - Question 2619 Array Prototype Last

### Attempt 1: 
```js
Array.prototype.last = function() {
    return this.length === 0 ? -1 : this[this.length - 1];
};
```
- Runtime: 39 ms (Beats: 97.58%)
- Memory: 48.59 MB (Beats: 68.14%)

<br>
