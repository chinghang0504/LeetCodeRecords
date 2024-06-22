# [LeetCode Records](../../README.md) - Question 2796 Repeat String

### Attempt 1: 
```js
String.prototype.replicate = function(times) {
    result = "";
    for (let i = 0; i < times; i++) {
        result += this;
    }
    return result;
}
```
- Runtime: 64 ms (Beats: 96.43%)
- Memory: 59.42 MB (Beats: 71.03%)

<br>
